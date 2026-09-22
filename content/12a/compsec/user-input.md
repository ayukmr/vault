# user input validation

## html

https://jennselby.github.io/ComputerSecurityCourseNotes/assets/code/comments.html

`<script>` tags don't run when they're inserted into the dom after the page loads, so instead I tried using other tags to run code. I found that `<img src=/ onerror="console.log('x')">` works well, where `console.log('x')` can be any arbitrary code, which runs since rendering the path "/" (the page itself) results in an error.

one way to fix this exploit is to use `innerText` instead of `innerHTML`. this should be done for the `dateDiv` regardless, but that would also prevent the use of basic markup tags in `textDiv`, which could be a feature of the comments. to both fix the code execution but still retain markup, I'd probably use a sanitization library that removes any html tags/attributes that can run js and then still use `innerHTML`. in this case, I used `dompurify`:

```js
import DOMPurify from 'dompurify';

document.getElementById('addComment').addEventListener(
    'click',
    function () {
        /* --snip-- */

        var dateDiv = document.createElement('div');
        dateDiv.innerText = Date();
        newDiv.appendChild(dateDiv);

        var textDiv = document.createElement('div');
        textDiv.innerHTML = DOMPurify.sanitize(document.getElementById('commentText').value);
        newDiv.appendChild(textDiv);

        /* --snip-- */
    }
);
```

the last way that it could be fixed is to have comments use a different markup type like markdown, which, if arbitrary tags are not allowed, restricts the possible html tags that can be put into the dom. so, only basic formatting like `<b>` and `<i>` would be allowed with `**x**` and `_x_` respectively.

## buffer overflow

https://jennselby.github.io/ComputerSecurityCourseNotes/assets/code/buffer_overflow.c

I added in a few more log statements to the program to make it a bit easier to figure out what's going on in `check_authentication`:
```c
int check_authentication(char *password) {
    int auth_flag = 0;
    char password_buffer[20];

    printf("buf ptr: %p\n", password_buffer);
    printf("auth flag ptr: %p\n", &auth_flag);

    strcpy(password_buffer, password);

    if (strcmp(password_buffer, "password") == 0) {
        auth_flag = 1;
        printf("set auth flag\n");
    }

    printf("auth flag val: %d\n", auth_flag);

    return auth_flag;
}
```

running with the correct password gives these logs which look right:
```
~/s/compsec ❱ ./a.out password
buf ptr: 0x16b59fcc0
auth flag ptr: 0x16b59fcd4
set auth flag
auth flag val: 1
Access Granted.
```

running with an incorrect password with length <= 20 gives this:
```
~/s/compsec ❱ ./a.out wrongpassword
buf ptr: 0x16ce5fcc0
auth flag ptr: 0x16ce5fcd4
auth flag val: 0
Access Denied.
```

but with a password with length > 20, it can get through:
```
~/s/compsec ❱ ./a.out verylongwrongpassword
buf ptr: 0x16f97fcb0
auth flag ptr: 0x16f97fcc4
auth flag val: 100
Access Granted.
```

as covered in class, this is because of a buffer overflow, since the buf ptr address is right before the auth flag ptr, so too long of a password overflows into the auth flag value and sets it to some arbitrary number. I was a bit confused, however, why the pointers would be arranged like this, since `auth_flag` is defined _before_ `password_buffer` in the code:
```c
int auth_flag = 0;
char password_buffer[20];
```

so, intuitively, I would think `&auth_flag < password_buffer`. I read up on this a little and the explanation is basically that in allocating addresses, the compiler will start at some pointer value (say, `p`) and start allocating _downwards_ from that. so `auth_flag` would get `p - 4` to `p` (exclusive) to work with, and `password_buffer` would get `p - 4 - 20` to `p - 4` (exclusive). so then, the collision works, since `password_buffer` runs into `auth_flag`. in comparison, if I reorder the definitions, the overflow no longer works, as the auth flag ptr comes first:
```
~/s/compsec ❱ ./a.out verylongwrongpassword
buf ptr: 0x16b287cb4
auth flag ptr: 0x16b287cb0
auth flag val: 0
Access Denied.
```

this could technically be seen as one way to solve this problem, albeit being a terrible, impractical solution that just moves the overflow problem somewhere else down the line. an actual decent way to fix it is to use `strncpy`, which fixes the length of the copied string, which means that copying `password` to `password_buffer` can't overflow. it would be used in the program as follows, as a literal one-line change:
```c
int check_authentication(char *password) {
    int auth_flag = 0;
    char password_buffer[20];

    printf("buf ptr: %p\n", password_buffer);
    printf("auth flag ptr: %p\n", &auth_flag);

    strncpy(password_buffer, password, 20);

    if (strcmp(password_buffer, "password") == 0) {
        auth_flag = 1;
        printf("set auth flag\n");
    }

    printf("auth flag val: %d\n", auth_flag);

    return auth_flag;
}
```

which now fixes the problem:
```
~/s/compsec ❱ ./a.out verylongwrongpassword
buf ptr: 0x16b68fcb0
auth flag ptr: 0x16b68fcc4
auth flag val: 0
Access Denied.
```

# subclasses

Subclasses model the inheritance of attributes.
<img src="assets/subclasses/1.png" width="300">

---

Let's start with a base `Animal` class.
<img src="assets/subclasses/2.png" width="400">

Like before, creating an instance.
<img src="assets/subclasses/3.png" width="450">

---

We're going to make `Cat` extend the properties of `Animal`.
<img src="assets/subclasses/4.png" width="350">

It can be thought of as copying over the variables and methods from `Animal`.
Notably, the `Animal` constructor gets renamed to `super`.
The cyan text doesn't actually exist in the code.
<img src="assets/subclasses/5.png" width="400">

We can create an instance of this `Cat` class.
`speak` is available since it is inherited from `Animal`.
<img src="assets/subclasses/6.png" width="350">

Note that every `Cat` is also an `Animal`.
They have the same properties and methods.
<img src="assets/subclasses/7.png" width="300">

---

For a more complex example, let's also include an extra field and method in a new version of `Cat`.
<img src="assets/subclasses/8.png" width="400">

We can now create this new `Cat`, giving it a whiskers count.
`speak` can be used based on the `Animal` superclass, and `age` was added for the `Cat` class.
<img src="assets/subclasses/9.png" width="350">

Like before, every `Cat` is also an `Animal`.
This relationship is always true for subclasses.
However, in this case, it also includes some extra things like `whiskers` and `age`.
<img src="assets/subclasses/10.png" width="300">

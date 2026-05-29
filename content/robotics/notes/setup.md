# dauntless setup

## building

(note: do **not** clone ayukmr/dauntless, that repo only contains the library)
```sh
$ git clone https://github.com/ayukmr/dauntless-srv
$ cd dauntless-srv
```

### locally

.envrc
```sh
export LIBCLANG_PATH="$(brew --prefix llvm)/lib"
export DYLD_LIBRARY_PATH="$LIBCLANG_PATH:$DYLD_LIBRARY_PATH"
```

### for pi

```sh
$ limactl create --name=default --arch=x86_64 template://ubuntu
```

`lima.yaml`
```yaml
mounts:
  - location: "~"
    writable: true
```

```sh
$ sudo apt install build-essential cmake

$ git clone https://github.com/opencv/opencv.git --branch 4.x
$ cd opencv
$ mkdir build && cd build

$ cmake .. \
  -DCMAKE_BUILD_TYPE=Release \
  -DBUILD_SHARED_LIBS=OFF \
  -DBUILD_TESTS=OFF \
  -DBUILD_PERF_TESTS=OFF \
  -DBUILD_opencv_highgui=OFF \
  -DBUILD_opencv_apps=OFF \
  -DCMAKE_INSTALL_PREFIX=/opt/opencv-static

$ make -j $(nproc)
$ sudo make install
```

```sh
$ sudo apt install libclang-dev
```

`.envrc`
```sh
export LIBCLANG_PATH=/usr/lib/llvm-20/lib
```

```sh
$ cargo build --release --target=aarch64-unknown-linux-gnu
```

## running

### copying to pi

```sh
$ ssh frc4904@dauntless.local # password: 4904
```

```sh
$ scp target/aarch64-unknown-linux-gnu/release/dauntless-srv frc4904@dauntless.local:/home/frc4904/dauntless
```

### running

`Rocket.toml`
```toml
[default]
address = "0.0.0.0"
log_level = "off"
```

```sh
$ ./dauntless
```

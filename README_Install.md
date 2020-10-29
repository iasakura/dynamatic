# Install

## Install LLVM

Install LLVM to `$LLVM_INSTALL_DIR`.

```
git clone http://llvm.org/git/llvm.git --branch release_60 --depth 1
cd llvm/tools
git clone http://llvm.org/git/clang.git --branch release_60 --depth 1
git clone http://llvm.org/git/polly.git --branch release_60 --depth 1
cd ..
mkdir _build && cd _build
cmake3 .. -DCMAKE_BUILD_TYPE=Debug -DLLVM_INSTALL_UTILS=ON -DLLVM_TARGETS_TO_BUILD="X86" -DCMAKE_INSTALL_PREFIX=$LLVM_INSTALL_DIR
make
make install
```

## Install Dynamatic

Install Dynamatic to `$DYNAMATIC_INSTALL_DIR`

```
git clone git@github.com:iasakura/dynamatic.git
mkdir build
cd build
cmake -DLLVM_DIR=$LLVM_INSTALL_DIR/lib/cmake/llvm -DCMAKE_INSTALL_PREFIX=$DYNAMATIC_INSTALL_DIR  ..
cmake --build . -t install -j4
```

## Usage

```
export PATH=$DYNAMATIC_INSTALL_DIR/bin
dynamatic
```


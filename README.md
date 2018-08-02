# MathX
函数计算

[![Travis](https://img.shields.io/travis/NextCodeX/MathX.svg?style=for-the-badge&maxAge=3600)](https://travis-ci.org/NextCodeX/MathX)

## Compile
``` sh
$ cmake .
```
> result
``` sh
-- The C compiler identification is AppleClang 9.1.0.9020039
-- The CXX compiler identification is AppleClang 9.1.0.9020039
-- Check for working C compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/cc
-- Check for working C compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/c++
-- Check for working CXX compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/zhoumq/projj/github.com/NextCodeX/MathX
```

## Install
``` sh
$ make install
```
> result
``` sh
[ 50%] Built target MathFunctions
Scanning dependencies of target MathX
[ 75%] Building CXX object CMakeFiles/MathX.dir/main.cc.o
[100%] Linking CXX executable MathX
[100%] Built target MathX
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/bin/MathX
-- Installing: /usr/local/include/config.h
-- Installing: /usr/local/lib/libMathFunctions.a
-- Installing: /usr/local/include/MathFunctions.h
```

## Test
``` sh
$ make test
```
> result
``` sh
Running tests...
Test project /Users/zhoumq/projj/github.com/NextCodeX/MathX
    Start 1: test_run
1/5 Test #1: test_run .........................   Passed    0.01 sec
    Start 2: test_usage
2/5 Test #2: test_usage .......................   Passed    0.01 sec
    Start 3: test_5_2
3/5 Test #3: test_5_2 .........................   Passed    0.01 sec
    Start 4: test_10_5
4/5 Test #4: test_10_5 ........................   Passed    0.01 sec
    Start 5: test_2_10
5/5 Test #5: test_2_10 ........................   Passed    0.00 sec

100% tests passed, 0 tests failed out of 5

Total Test time (real) =   0.04 sec
```

## Packaging
1. 打包
生成二进制安装包
``` sh
$ cpack -C CPackConfig.cmake
```

生成源码安装包
``` sh
$ cpack -C CPackSourceConfig.cmake
```

> result
``` sh
CPack: Create package using STGZ
CPack: Install projects
CPack: - Run preinstall target for: MathX
CPack: - Install project: MathX
CPack: Create package
CPack: - package: /Users/zhoumq/projj/github.com/NextCodeX/MathX/MathX-0.1.1-Darwin.sh generated.
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: MathX
CPack: - Install project: MathX
CPack: Create package
CPack: - package: /Users/zhoumq/projj/github.com/NextCodeX/MathX/MathX-0.1.1-Darwin.tar.gz generated.
```

2. 安装
安装二进制包

``` sh
$ sh MathX-0.1.1-Darwin.sh
```

> result
``` sh
MathX Installer Version: 0.1.1, Copyright (c) Humanity
This is a self-extracting archive.
The archive will be extracted to: /Users/zhoumq/projj/github.com/NextCodeX/MathX

If you want to stop extracting, please press <ctrl-C>.
MIT License

Copyright (c) 2018 开源小队

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


Do you accept the license? [yN]:
y
By default the MathX will be installed in:
  "/Users/zhoumq/projj/github.com/NextCodeX/MathX/MathX-0.1.1-Darwin"
Do you want to include the subdirectory MathX-0.1.1-Darwin?
Saying no will install in: "/Users/zhoumq/projj/github.com/NextCodeX/MathX" [Yn]:
Y

Using target directory: /Users/zhoumq/projj/github.com/NextCodeX/MathX/MathX-0.1.1-Darwin
Extracting, please wait...

Unpacking finished successfully
```

## Author
MathX © [NextCodeX](https://github.com/NextCodeX), Released under the MIT License. 

#Development Notes
##Build openssl
* Download [openssl](https://github.com/openssl/openssl/releases)
* Install [perl](http://www.activestate.com/ActivePerl)
* Build steps based [from here](http://charette.no-ip.com:81/programming/2015-04-09_OpenSSL/)
###Win64 version
* In a text editor, open ms/nt.mak and replace all occurrences of /Zi with /Z7 except on the line starting with ASM.
* Then run the following commands in openssl folder:

**Debug version:**
```
perl Configure no-asm no-shared debug-VC-WIN64A --prefix=builds\build-debug
ms\do_win64a.bat
"C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\vcvarsall.bat"
nmake -f ms\nt.mak clean
nmake -f ms\nt.mak
nmake -f ms\nt.mak install
```
**Release version:**
```
perl Configure no-asm no-shared VC-WIN64A --prefix=builds\build-release
ms\do_win64a.bat
"C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\vcvarsall.bat"
nmake -f ms\nt.mak clean
nmake -f ms\nt.mak
nmake -f ms\nt.mak install
```
##Build rabbitmq-c
* Download [rabbitmq-c](https://github.com/alanxz/rabbitmq-c/releases)
* Install [CMake v2.6 or better](https://cmake.org/)
* Ensure that cmake bin folder is in your PATH
###Win64 version
* Execute those command in the rabbitmq-c folder:

**Debug version:**
```
mkdir build-debug
cd build-debug
```
Define where is located Debug *openssl* library and Configure build, cmake Visual Studio generators *-G <generator>* can be found [here](https://cmake.org/cmake/help/v3.6/manual/cmake-generators.7.html#visual-studio-generators)
```
cmake -DOPENSSL_ROOT_DIR=C:\apis\openssl-1.0.2l -DOPENSSL_LIBRARIES=C:\apis\openssl-1.0.2l\libd -G "Visual Studio 11 2012 Win64" ..
```
```
cmake --build . --config Debug --target rabbitmq-static --clean-first
```
**Release version:**
```
mkdir build-release
cd build-release
```
Define where is located Release *openssl* library
```
cmake -DOPENSSL_ROOT_DIR=C:\apis\openssl-1.0.2l -DOPENSSL_LIBRARIES=C:\apis\openssl-1.0.2l\lib -G "Visual Studio 11 2012 Win64" ..
```
```
cmake --build . --config Release --target rabbitmq-static --clean-first
```

##Build amqcpp
**Debug version:**
```
mkdir build-debug
cd build-debug
```
Define where is located Debug *openssl* library and Configure build, cmake Visual Studio generators *-G <generator>* can be found [here](https://cmake.org/cmake/help/v3.6/manual/cmake-generators.7.html#visual-studio-generators)
```
cmake -DOPENSSL_ROOT_DIR=C:\apis\openssl-1.0.2l -DOPENSSL_LIBRARIES=C:\apis\openssl-1.0.2l\libd -DRABBITMQ_ROOT_DIR=C:\apis\rabbitmq-c-0.8.0 -DRABBITMQ_LIBRARY=C:\apis\rabbitmq-c-0.8.0\libd -G "Visual Studio 11 2012 Win64" ..
```
```
cmake --build . --config Debug --target amqpcpp --clean-first
```

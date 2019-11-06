# Proj4 CMake example
This repo shows a minimum working example program in C++ using the [proj4][2] library. The example program is acutally taken (copied) from [gis.stackexchange][0]. The tiny contribution of this repo is just a suggestion on how to install the [proj4][2] library and how to compile an application using the library with CMake.

## 1. Installing proj4
I recommend using the C++ package manager [vcpkg][1]. Please follow the quick start section on the [vcpkg][1] repo to install it. 

Afterwards execute `./vcpkg install proj4` to install the [proj4][2] library.

[0]:https://gis.stackexchange.com/questions/58555/proj4-c-api-amersfoort-rd-new-to-wgs84
[1]:https://github.com/microsoft/vcpkg
[2]:https://proj.org/

## 2. Compiling the example program
Clone this repo, cd into it, create a build directory and call cmake from there:
```
Linux:~/$ git clone https://github.com/thomasfermi/proj4_cmake_example.git
Linux:~/$ cd proj4_cmake_example
Linux:~/$ mkdir build
Linux:~/$ cd build
Linux:~/$ cmake .. "-DCMAKE_TOOLCHAIN_FILE=/home/my_user_name/vcpkg/scripts/buildsystems/vcpkg.cmake"
```
In the last command I assumed that you have your vcpkg installation under `/home/my_username/vcpkg`. Change the command according to your actual installation path (the path to where you cloned the vcpkg github repo). If CMake did not finish successfully, please check out the appendix of this README.md. If CMake did finish successfully, you can execute
```
Linux:~/$ make
```
Hopefully compilation will be successful and you can execute the example program and see the following output
```
Linux:~/$ ./example_main
0
5.14431
52.1976
```

### Appendix: Clang Compiler
In the CMakeLists.txt there is a command `SET(CMAKE_CXX_COMPILER /usr/bin/clang++)`. You might want to change `usr/bin/clang++` to the path of your favorite C++ compiler. Note that I had trouble linking the libraries with `g++`. That is why I chose `clang++`. Check out this [stackoverflow answer][3] for more details.

[3]:https://stackoverflow.com/a/51008697/2609987

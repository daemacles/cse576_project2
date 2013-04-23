Compiling with CMake
====================

The folder `PanoramaSkel` has a `CMakeLists.txt` file in it.  Go there and

Linux
-----

    $ mkdir build
    $ cd build
    $ cmake ..
    $ make -j<number of cores>

Your `Panorama` executable will be in the `build/` directory.

Windows VC++
------------

First, [download cmake](http://www.cmake.org/cmake/resources/software.html),
install it (ensuring that you have added cmake to the system PATH) and run in
a console:
    
    C:\<path to this repository\> cmake -G "Visual Studio 11"

This will build a .sln file for Visual Studio 2012, you may then enter the
`Debug` folder and run `Panorama.exe` from the command prompt to run the
executable

Compiling with Make
===================

This Makefile will track dependencies.

Linux
-----

As usual, go to `PanoramaSkel` and

    $ make -j<number of cores>

Adding new Files
================

Add your new .cpp files to either `CMakeFiles.txt` or `Makefile` respectively.
Don't worry about header files, they are automatically tracked with either
method.

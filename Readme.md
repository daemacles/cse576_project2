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

I have no idea, sorry.  But it works, they assure me.

Compiling with Make
===================

This isn't too recommended because the default `Makefile`s aren't that great.
Feel free to contribute better ones.

Linux
-----

As usual, go to `PanoramaSkel` and

    $ make -j<number of cores>
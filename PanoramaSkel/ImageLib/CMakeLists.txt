
add_library (ImageLib Convolve.cpp FileIO.cpp Image.cpp ImageProc.cpp
                      RefCntMem.cpp Transform.cpp)

if( MSVC )
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /D_CRT_SECURE_NO_WARNINGS")
endif()

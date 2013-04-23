cmake_minimum_required (VERSION 2.6)

project (Panorama)

include_directories ("${PROJECT_SOURCE_DIR}/ImageLib")

find_package (OpenGL REQUIRED)

if (CMAKE_COMPILER_IS_GNUCC)
    execute_process(COMMAND ${CMAKE_C_COMPILER} -dumpversion OUTPUT_VARIABLE GCC_VERSION)
    if (GCC_VERSION VERSION_GREATER 4.7 OR GCC_VERSION VERSION_EQUAL 4.7 )
        set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
    endif()
endif()

add_subdirectory (ImageLib)

add_executable (Panorama BlendImages.cpp
                         FeatureAlign.cpp
                         FeatureSet.cpp
                         WarpSpherical.cpp
                         Project2.cpp)

if( MSVC )
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /D_CRT_SECURE_NO_WARNINGS")
    target_link_libraries (Panorama ImageLib)
else()
    target_link_libraries (Panorama ImageLib png jpeg X11 Xext Xi Xmu)
endif()

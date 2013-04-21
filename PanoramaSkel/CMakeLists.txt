cmake_minimum_required (VERSION 2.6)

project (Panorama)

include_directories ("${PROJECT_SOURCE_DIR}/ImageLib")

find_package (OpenGL REQUIRED)

if (CMAKE_COMPILER_IS_GNUCC)
   set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif (CMAKE_COMPILER_IS_GNUCC)

add_subdirectory (ImageLib)

add_executable (Panorama BlendImages.cpp
                         FeatureAlign.cpp
                         FeatureSet.cpp
                         WarpSpherical.cpp
                         Project2.cpp)

target_link_libraries (Panorama ImageLib png jpeg X11 Xext Xi Xmu)


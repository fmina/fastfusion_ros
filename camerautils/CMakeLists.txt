cmake_minimum_required(VERSION 2.8)
project(camerautils)
set(CMAKE_BUILD_TYPE Release)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

add_definitions(-std=c++11)

find_package(Eigen REQUIRED)
include_directories(${Eigen_INCLUDE_DIRS})

cs_add_library(camerautils STATIC
						src/camerautils.cpp)

cs_install()
cs_export()

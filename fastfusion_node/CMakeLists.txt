cmake_minimum_required(VERSION 2.8)
project(fastfusion_node)

#################################################
# 	Perform all set commands                   	#
#################################################
set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
#set(CMAKE_BUILD_TYPE Debug)
set(OpenCV_LIBS opencv_core opencv_imgproc opencv_highgui opencv_calib3d)
#set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -mavx2 -funroll-loops -DOWNAVX")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -mavx2 -funroll-loops -DOWNAVX")
if(UNIX AND NOT APPLE)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp")
  set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fopenmp")
endif()
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -msse4.2 -funroll-loops")

#################################################
#	Find the necessary Pkgs 					#
#################################################
find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

add_definitions(-std=c++11)

#################################################
# 	Include Directories 	                   	#
#################################################


#################################################
# 	Add Executables 	 	                   	#
#################################################
cs_add_executable(fastfusion_node
				src/main_fastfusion_node.cpp
				src/fastfusion_node.cpp
				src/online_fusion_ros.cpp)



#################################################
# 	Link to target Libraries                   	#
#################################################


cs_install()
cs_export()

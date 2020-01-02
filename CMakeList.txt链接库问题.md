# CMakeList.txt

## PCL

~~~cmake
cmake_minimum_required(VERSION 3.14)
project(PCLDemo)
set(CMAKE_CXX_STANDARD 14)

# 设置输出根目录为build/Debug
set(OUTPUT_DIRECTORY_ROOT ${CMAKE_CURRENT_SOURCE_DIR}/build/${CMAKE_BUILD_TYPE})
# 设置可执行程序输出到build/Debug/bin目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${OUTPUT_DIRECTORY_ROOT}/bin" CACHE PATH "Runtime directory" FORCE)
# 设置库文件输出到build/Debug/lib目录
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${OUTPUT_DIRECTORY_ROOT}/lib" CACHE PATH "Library directory" FORCE)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${OUTPUT_DIRECTORY_ROOT}/lib" CACHE PATH "Archive directory" FORCE)

find_package(PCL REQUIRED)
# 包含头文件目录
include_directories(${PCL_INCLUDE_DIRS})
# 设置依赖库链接目录
link_directories(${PCL_LIBRARY_DIRS})
# 添加预处理器和编译器标记
add_definitions(${PCL_DEFINITIONS})

add_executable(PCLDemo main.cpp)
target_link_libraries(PCLDemo ${PCL_LIBRARIES})
~~~

## opencv

~~~cmake
#指定opencv的版本和路径
find_package(OpenCV 4.0 REQUIRED PATHS "/path/2/opencv/install/path")
#寻找opencv库
find_package(OpenCV REQUIRED)
#message(STATUS ${OpenCV_INCLUDE_DIRS})
message("OpenCV_LIBS = ${OpenCV_LIBS}")
#添加头文件
include_directories(${OpenCV_INCLUDE_DIRS})
#链接Opencv库
target_link_libraries(realsense ${OpenCV_LIBS})
~~~

## eigen3

~~~cmake
include_directories(${PCL_INCLUDE_DIRS} ${EIGEN3_INCLUDE_DIR})
~~~

## boost

~~~cmake
find_package(Boost 1.55.0 REQUIRED COMPONENTS system filesystem)
include_directories( ${Boost_INCLUDE_DIRS})
link_directories( ${Boost_LIBRARY_DIRS})

target_link_libraries(kinect1 ${Boost_LIBRARIES})
~~~

## realsense2

~~~cmake
# Find librealsense2 installed package
find_package(realsense2 REQUIRED)

# Enable C++11
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# Link librealsense2 to the target
target_link_libraries(${PROJECT_NAME} ${realsense2_LIBRARY})
~~~


cmake_minimum_required(VERSION 2.8.3)
project(visual_servo)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH}  ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -fPIC")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIC")
add_compile_options(-O3 -g -DNDEBUG -pthread)

find_package(Boost REQUIRED)
find_package(OpenCV REQUIRED)
find_package(Eigen3 REQUIRED)

include_directories(
    include
    ${Boost_INCLUDE_DIRS}
    ${OpenCV_INCLUDE_DIRS}
)

add_executable(StereoVisionforADAS
    main.cpp
    StereoMatching.cpp
    StereoVisionForADAS.cpp
    StixelEstimation.cpp
    StixelSegmentation.cpp)

target_link_libraries(StereoVisionforADAS
  ${OpenCV_LIBRARIES}
  )

cmake_minimum_required(VERSION 3.12)
project(USAC_1_0)

set(CMAKE_CXX_STANDARD 14)

find_package(OpenCV 3 REQUIRED)
include_directories(SYSTEM ${OpenCV_INCLUDE_DIRS})

set(SRC_DIR ${CMAKE_SOURCE_DIR}/GraphCutRANSAC)

include_directories(${SRC_DIR})

add_library(gc_ransac SHARED
        ${SRC_DIR}/5point.cpp
        ${SRC_DIR}/essential_estimator.cpp
        ${SRC_DIR}/fundamental_estimator.cpp
        ${SRC_DIR}/homography_estimator.cpp
        ${SRC_DIR}/line_estimator.cpp
        ${SRC_DIR}/GCoptimization.cpp
        ${SRC_DIR}/GCRANSAC.cpp
        ${SRC_DIR}/LinkedBlockList.cpp
        ${SRC_DIR}/maxflow.cpp
        ${SRC_DIR}/Rpoly.cpp
        #${SRC_DIR}/stdafx.cpp
        ${SRC_DIR}/graph.cpp)
target_link_libraries(gc_ransac ${OpenCV_LIBRARIES})

add_executable(test ${SRC_DIR}/main.cpp)
target_link_libraries(test gc_ransac)


# disable in source compile, prevent conflicts with source file directories
if("${CMAKE_SOURCE_DIR}" STREQUAL "${CMAKE_BINARY_DIR}")
    message(FATAL_ERROR "in-source builds are not allowed.
    You should create a separate directory for build files.")
endif()

if(CMAKE_GENERATOR MATCHES Xcode)
    cmake_minimum_required(VERSION 3.12)
else()
    cmake_minimum_required(VERSION 3.10)
endif()
message(STATUS "CMAKE_INSTALL_PREFIX = ${CMAKE_INSTALL_PREFIX}")



project(retinaface)
include_directories(${PROJECT_SOURCE_DIR}/../ncnn/include/ncnn)
link_directories( ${PROJECT_SOURCE_DIR}/../ncnn/lib)
add_executable(retinaface  retinaface.cpp)
#target_include_directories( retinaface PUBLIC ${PROJECT_SOURCE_DIR}/../ncnn/include/ncnn)

#target_compile_definitions(retinaface  PUBLIC USE_NCNN_SIMPLEOCV)

# include_directories(../ncnn/include/ncnn)
#link_directories(retinaface ${PROJECT_SOURCE_DIR}/../ncnn/lib)

target_link_libraries(retinaface  -lncnn)

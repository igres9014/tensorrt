cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}" ${CMAKE_MODULE_PATH})
set(TensorRT_DIR "~/TensorRT-8.2.1.8")

include_directories("~/TensorRT-8.2.1.8/include")
link_directories("~/TensorRT-8.2.1.8/lib")

project(TensorRTSample)

find_package(Threads)
find_package(CUDA REQUIRED)
find_package(OpenCV REQUIRED)
#find_package(TensorRT REQUIRED)

# TARGETS --------------------------------------------------------------------------------------------------------------
add_executable(trt_sample main_raw.cpp)
target_include_directories(trt_sample PUBLIC ${OpenCV_INCLUDE_DIRS} ${CUDA_INCLUDE_DIRS} ${TensorRT_DIR})
target_link_libraries(trt_sample PUBLIC ${OpenCV_LIBS} ${CUDA_LIBRARIES} ${CMAKE_THREAD_LIBS_INIT})
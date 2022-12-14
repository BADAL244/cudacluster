cmake_minimum_required(VERSION 2.8 FATAL_ERROR)



project(playback)
find_package(CUDA 11.4 REQUIRED)
include_directories("${CUDA_INCLUDE_DIRS}")
find_package(PCL 1.2 REQUIRED)
find_library(SSL NAMES cudacluster PATHS ${CMAKE_SOURCE_DIR}/lib)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})
list(REMOVE_ITEM PCL_LIBRARIES "vtkproj4")
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/lib/)
LINK_DIRECTORIES(${CMAKE_SOURCE_DIR}/lib/)


add_executable (environment src/newmain.cpp)
target_link_libraries (environment ${PCL_LIBRARIES} ${CUDA_LIBRARIES} ${SSL})

cmake_minimum_required( VERSION 2.8)

project(Phase_Shift)

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

# pcl
find_package(PCL REQUIRED COMPONENT common io)
find_package(PCL 1.7 REQUIRED)
include_directories( ${PCL_INCLUDE_DIRS})
add_definitions( ${PCL_DEFINITIONS})


add_executable(Phase_Shift main.cpp)
add_library(Camera_Calib_LIB CameraCalib.cpp)
add_library(CalPhase_LIB CalPhase.cpp)
add_library(ProPoint_LIB Propointcloud.cpp)

target_link_libraries(Phase_Shift ${OpenCV_LIBS} ${PCL_LIBRARIES})
target_link_libraries(Phase_Shift Camera_Calib_LIB)
target_link_libraries(Phase_Shift CalPhase_LIB)
target_link_libraries(Phase_Shift ProPoint_LIB)


install(TARGETS Phase_Shift RUNTIME DESTINATION bin)

cmake_minimum_required(VERSION 2.8.3)
project(udacity_bot)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
    message_generation
    geometry_msgs
    std_msgs
    actionlib
    move_base_msgs
    roscpp
    tf
    laser_geometry
)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
## System dependencies are found with CMake's conventions
 find_package(Boost REQUIRED COMPONENTS system)
 find_package(cmake_modules REQUIRED)
 find_package(Eigen REQUIRED)


generate_messages(
    DEPENDENCIES
    std_msgs
    geometry_msgs
    move_base_msgs
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES udacity_bot
#  CATKIN_DEPENDS other_catkin_pkg
#  DEPENDS system_lib
)

include_directories(
	include
	${catkin_INCLUDE_DIRS}
	${Eigen_INCLUDE_DIRS}
)

add_executable(navigation_goal src/navigation_goal.cpp)
target_link_libraries(navigation_goal ${catkin_LIBRARIES})


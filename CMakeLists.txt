cmake_minimum_required(VERSION 2.8.3)
project(visual_localization)

find_package(catkin REQUIRED
        COMPONENTS
            angles
            geometry_msgs
            message_filters
            nav_msgs
            rosconsole
            roscpp
            rospy
            tf
        )


find_package(Boost REQUIRED COMPONENTS signals)

catkin_package(
    CATKIN_DEPENDS
        geometry_msgs
        nav_msgs
        roscpp
        rospy
)

include_directories(${catkin_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})

add_executable(visual_localization src/optical_fake_localization.cpp)
target_link_libraries(visual_localization
    ${catkin_LIBRARIES}
    ${Boost_LIBRARIES}
    )
add_dependencies(visual_localization ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})


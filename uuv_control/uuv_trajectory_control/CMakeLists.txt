cmake_minimum_required(VERSION 2.8.3)
project(uuv_trajectory_control)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED)

## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)

catkin_python_setup()

catkin_package()

catkin_install_python(PROGRAMS scripts/rov_nl_pid_controller.py
                               scripts/rov_mb_sm_controller.py
                               scripts/rov_nmb_sm_controller.py
                               scripts/rov_pid_controller.py
                               scripts/demo_wp_trajectory_generator.py
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

install(DIRECTORY config
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
        PATTERN "*~" EXCLUDE)

if (CATKIN_ENABLE_TESTING)
  catkin_add_nosetests(tests/test_waypoint.py)
  catkin_add_nosetests(tests/test_trajectory_point.py)
  catkin_add_nosetests(tests/test_waypoint_set.py)
endif()

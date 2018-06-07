# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 2.8.3)
project(dynamixel_driver)

find_package(catkin REQUIRED COMPONENTS
  rospy
  std_msgs
  message_generation
)

catkin_python_setup()

add_service_files(
  FILES
  SetMotorOffset.srv
)

generate_messages( DEPENDENCIES std_msgs )

catkin_package(
    CATKIN_DEPENDS rospy diagnostic_msgs message_runtime
)

install(PROGRAMS
  scripts/change_id.py
  scripts/info_dump.py
  scripts/set_servo_config.py
  scripts/set_torque.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

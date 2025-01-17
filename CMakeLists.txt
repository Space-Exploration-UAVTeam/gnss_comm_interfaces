cmake_minimum_required(VERSION 3.5)
project(gnss_comm_interfaces)

# to make sure ccache produces colorized output.
add_compile_options(-fdiagnostics-color=always)

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)

set(msg_files
  "msg/GnssTimeMsg.msg"
  "msg/GnssEphemMsg.msg"
  "msg/GnssGloEphemMsg.msg"
  "msg/GnssMeasMsg.msg"
  "msg/GnssObsMsg.msg"
  "msg/GnssBestXYZMsg.msg"
  "msg/GnssPVTSolnMsg.msg"
  "msg/GnssSvsMsg.msg"
  "msg/GnssTimePulseInfoMsg.msg"
  "msg/StampedFloat64Array.msg"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES
  std_msgs
)

ament_export_dependencies(rosidl_default_runtime)
ament_package()


set(MOVEIT_LIB_NAME moveit_robot_state_rviz_plugin)
add_library(${MOVEIT_LIB_NAME}_core 
  src/robot_state_display.cpp  
  include/moveit/robot_state_rviz_plugin/robot_state_display.h)
target_link_libraries(${MOVEIT_LIB_NAME}_core moveit_rviz_plugin_render_tools 
  ${catkin_LIBRARIES} ${OGRE_LIBRARIES} ${QT_LIBRARIES} ${Boost_LIBRARIES})

add_library(${MOVEIT_LIB_NAME} src/plugin_init.cpp)
target_link_libraries(${MOVEIT_LIB_NAME} ${MOVEIT_LIB_NAME}_core ${catkin_LIBRARIES} ${Boost_LIBRARIES})

install(DIRECTORY include/ DESTINATION include)

install(TARGETS ${MOVEIT_LIB_NAME}_core ${MOVEIT_LIB_NAME}
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION})


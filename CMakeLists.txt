cmake_minimum_required(VERSION 3.8)
project(whisker_project)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


# Install launch files (if you have any in a 'launch' directory)
#find_package(launch REQUIRED)
#install(DIRECTORY launch
#  DESTINATION share/${PROJECT_NAME}/launch)

# Install parameter files (if you have any in a 'config' or 'param' directory)
install(DIRECTORY config
  DESTINATION share/${PROJECT_NAME}/config)

# Install URDF files
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/urdf/whisker_project.urdf  # Replace with your URDF filename
  DESTINATION share/${PROJECT_NAME}/urdf)

# Install mesh files (you might need to list individual files or use glob)
install(DIRECTORY meshes
  DESTINATION share/${PROJECT_NAME}
  FILES_MATCHING PATTERN "*.stl" PATTERN "*.STL"
                         PATTERN "*.dae" PATTERN "*.DAE")

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()

cmake_minimum_required(VERSION 2.6)
project(STLSoft C CXX)

set(STLSoft_VERSION 1.9.125)

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
  "${CMAKE_CURRENT_BINARY_DIR}/cmake/STLSoftConfigVersion.cmake"
  VERSION ${STLSoft_VERSION}
  COMPATIBILITY AnyNewerVersion
)
export(PACKAGE STLSoft)

set(PACKAGE_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include")
configure_file(cmake/STLSoftConfig.cmake.in
  "${CMAKE_CURRENT_BINARY_DIR}/cmake/STLSoftConfig.cmake"
  @ONLY
)

set( ConfigPackageLocation cmake/STLSoft)
install( DIRECTORY
    "${CMAKE_CURRENT_SOURCE_DIR}/include"
  DESTINATION ${CMAKE_INSTALL_PREFIX}
  COMPONENT Devel
)
install( FILES
    "${CMAKE_CURRENT_BINARY_DIR}/cmake/STLSoftConfig.cmake"
    "${CMAKE_CURRENT_BINARY_DIR}/cmake/STLSoftConfigVersion.cmake"
  DESTINATION ${ConfigPackageLocation}
  COMPONENT Devel
)



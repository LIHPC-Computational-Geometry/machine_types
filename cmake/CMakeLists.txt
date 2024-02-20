
include(CMakePackageConfigHelpers)

configure_package_config_file(MachineTypesConfig.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/MachineTypesConfig.cmake
  INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/MachineTypes/cmake)

write_basic_package_version_file(
  ${CMAKE_CURRENT_BINARY_DIR}/MachineTypesConfigVersion.cmake
  COMPATIBILITY SameMinorVersion # AnyNewerVersion|SameMajorVersion|SameMinorVersion|ExactVersion
  VERSION "${MachineTypes_VERSION}")

install(FILES
  ${CMAKE_CURRENT_BINARY_DIR}/MachineTypesConfig.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/MachineTypesConfigVersion.cmake
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/MachineTypes/cmake)

install(EXPORT MachineTypesTargets
  NAMESPACE MachineTypes::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/MachineTypes/cmake)

set(INC_FILES inc/machine_types.h)

add_library(MachineTypes INTERFACE)
add_library(MachineTypes::MachineTypes ALIAS MachineTypes)

target_include_directories(MachineTypes INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/inc>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}/inc>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

# target_link_libraries(mytestlib
#   PUBLIC Some_Lib_Used_in_Public_Headers
#   PRIVATE Some_Lib_Used_Internaly
# )

#install(DIRECTORY
#  ${CMAKE_CURRENT_SOURCE_DIR}/inc/
#  ${CMAKE_CURRENT_BINARY_DIR}/inc/
#  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
#  FILES_MATCHING PATTERN "*.h"
#  )
install(FILES
  ${INC_FILES}
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
  )


install(TARGETS MachineTypes
  EXPORT MachineTypesTargets
  )

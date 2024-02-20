cmake_minimum_required(VERSION 3.20)

include(CMakePrintHelpers)

#
# Change default CMake options for convenience
#

# Change default build type
set(CMAKE_BUILD_TYPE RelWithDebInfo CACHE STRING "Build type")

# Build .so by default
set(BUILD_SHARED_LIBS ON CACHE BOOL "Build shared libs")

# Build tests by default
set(BUILD_TESTING ON CACHE BOOL "Build tests")

# Build -fPIC by default (even static) by default
set(CMAKE_POSITION_INDEPENDENT_CODE ON CACHE BOOL "Position independent code")

# Silent some install messages by default
set(CMAKE_INSTALL_MESSAGE "LAZY" CACHE STRING "")

# Add rpaths of external dependencies by default
if (NOT DEFINED CMAKE_INSTALL_RPATH_USE_LINK_PATH)
  set(CMAKE_INSTALL_RPATH_USE_LINK_PATH ON) # not CACHE, only for our project
endif()

#
# Read the version from version.txt
#

file(READ "version.txt" version_txt)
string(REGEX REPLACE "^[ \t\n]+|[ \t\n]+$" "" version_txt "${version_txt}") # Strip

#
#
#

project(MachineTypes
  LANGUAGES C
  VERSION "${version_txt}"
  DESCRIPTION "Simple C numeric types definitions")

cmake_print_variables(MachineTypes_VERSION)

# (after project() is important here:)
include(GNUInstallDirs)

# Global PRIVATE compilation flags
add_compile_options(-Wall -Wextra)

add_subdirectory(machinetypes)
add_subdirectory(cmake)

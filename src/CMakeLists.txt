##############################################################################
# FILE:        moos-ivp-extend/src/CMakeLists.txt
# DATE:        2010/09/07
# DESCRIPTION: CMakeLists.txt file for the moos-ivp-extend source directory
##############################################################################

#============================================================================
# Add CMake modules that do not come with the system
#============================================================================
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/src/cmake_modules/")

#============================================================================
# List the subdirectories to build...
#============================================================================

## Feb'16: add process to convert a lon/lat location to x/y wpt update
#find_package(MOOSGeodesy)
#if ( MOOSGeodesy_FOUND )
#  include_directories(${MOOSGeodesy_INCLUDE_DIRS})
#  link_directories(${MOOSGeodesy_LIBRARY_PATH})
#  message("MOOSGeodesy_INCLUDE_DIRS:" ${MOOSGeodesy_INCLUDE_DIRS})
#  message("MOOSGeodesy_LIBRARY_PATH:" ${MOOSGeodesy_LIBRARY_PATH})
#  add_subdirectory(pLonLatToWptUpdate)
#endif()

# Sept'16: add process that can publish a certain var/val set,
#          X seconds after it received the publishing of another var/val set
add_subdirectory(pPublishAfterX)


##############################################################################
#                           END of CMakeLists.txt
##############################################################################

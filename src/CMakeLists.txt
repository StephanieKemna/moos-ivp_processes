##############################################################################
# FILE:        moos-ivp-extend/src/CMakeLists.txt
# DATE:        2010/09/07
# DESCRIPTION: CMakeLists.txt file for the moos-ivp-extend source directory
##############################################################################

#============================================================================
# Add the libraries in the current directory to the include path
#============================================================================
FILE(GLOB LOCAL_LIBRARY_DIRS ./lib_*)
INCLUDE_DIRECTORIES(${LOCAL_LIBRARY_DIRS})
INCLUDE_DIRECTORIES(./utils)

#============================================================================
# Add CMake modules that do not come with the system
#============================================================================
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/src/cmake_modules/")

#============================================================================
# List the subdirectories to build...
#============================================================================

# utils dir
ADD_SUBDIRECTORY(utils)

# Feb'16: process to convert a lon/lat location to x/y wpt update
find_package(MOOSGeodesy)
if ( MOOSGeodesy_FOUND )
  include_directories(${MOOSGeodesy_INCLUDE_DIRS})
  link_directories(${MOOSGeodesy_LIBRARY_PATH})
  message("MOOSGeodesy_INCLUDE_DIRS:" ${MOOSGeodesy_INCLUDE_DIRS})
  message("MOOSGeodesy_LIBRARY_PATH:" ${MOOSGeodesy_LIBRARY_PATH})
  add_subdirectory(pLonLatToWptUpdate)
endif()

# Sept'16: process that can publish a certain var/val set,
#          X seconds after it received the publishing of another var/val set
add_subdirectory(pPublishAfterX)

# find boost
SET(BOOST_MIN_VERSION "1.56.0")
find_package(Boost)
# Nov'15-Aug'17: simulation biology
if ( Boost_FOUND )
  ADD_SUBDIRECTORY(uSimBioSensor)
endif()

##############################################################################
#                           END of CMakeLists.txt
##############################################################################

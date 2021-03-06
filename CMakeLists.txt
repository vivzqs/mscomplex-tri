#Define the project we are working on
project(mscomplex-tri)

# Look for various software we need
cmake_minimum_required(VERSION 2.6)

set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} " -frounding-math -std=c++0x")

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)


# Handle installation paths
set(MSCOMPLEX_TRI_INSTALL_DIR "" CACHE PATH "installation dir")

if(MSCOMPLEX_TRI_INSTALL_DIR)
  set(MSCOMPLEX_TRI_INSTALL_DIR_BIN   ${MSCOMPLEX_TRI_INSTALL_DIR})
  set(MSCOMPLEX_TRI_INSTALL_DIR_LIB   ${MSCOMPLEX_TRI_INSTALL_DIR})
  set(MSCOMPLEX_TRI_INSTALL_DIR_SHARE ${MSCOMPLEX_TRI_INSTALL_DIR})
else(MSCOMPLEX_TRI_INSTALL_DIR)
  set(MSCOMPLEX_TRI_INSTALL_DIR_BIN   bin)
  set(MSCOMPLEX_TRI_INSTALL_DIR_LIB   lib)
  set(MSCOMPLEX_TRI_INSTALL_DIR_SHARE share/mscomplex-tri)
endif(MSCOMPLEX_TRI_INSTALL_DIR)

add_subdirectory(core)

option(BUILD_VIEWER "build the mscomplex viewer" OFF)
if(BUILD_VIEWER)
add_subdirectory(viewer)
endif(BUILD_VIEWER)

option(BUILD_PYMSTRI "mstri python module" OFF)
if(BUILD_PYMSTRI)
add_subdirectory(pymstri)
endif(BUILD_PYMSTRI)




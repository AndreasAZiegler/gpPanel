# -*- mode: cmake; -*-

## CMake pre-settings
cmake_minimum_required(VERSION 2.6)
cmake_policy(VERSION 2.6)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

############################################################
## Project setup
project(gpPanel CXX)
set(gpPanel_VERSION_MAJOR    0)
set(gpPanel_VERSION_MINOR    0)
set(gpPanel_VERSION_REVISION 0)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH    ${PROJECT_BINARY_DIR}/lib)

## install dirs
# libexec = /usr/lib/midas
if(NOT DEFINED INSTALL_LIBEXECDIR)
  message(STATUS "Set default libexec as prefix")
  set(INSTALL_LIBEXECDIR "${CMAKE_INSTALL_PREFIX}")
endif(NOT DEFINED INSTALL_LIBEXECDIR)
# libdir = ${libexec}/lib
set(INSTALL_LIBDIR "${INSTALL_LIBEXECDIR}/lib")
# incdir = ${libexec}/include
if(NOT DEFINED INSTALL_INCLUDEDIR)
  set(INSTALL_INCLUDEDIR "${INSTALL_LIBEXECDIR}/include")
endif(NOT DEFINED INSTALL_INCLUDEDIR)
# datadir = ${libexec}/share or ${prefix}/share/gpPanel
if(NOT DEFINED INSTALL_DATADIR)
  set(INSTALL_DATADIR "${CMAKE_INSTALL_PREFIX}/share/gpPanel")
endif(NOT DEFINED INSTALL_DATADIR)
# docdir = ${prefix}/share/doc/gpPanel
if(NOT DEFINED INSTALL_DOCDIR)
  set(INSTALL_DOCDIR "${CMAKE_INSTALL_PREFIX}/share/doc/gpPanel")
endif(NOT DEFINED INSTALL_DOCDIR)

################################################################
## Include utilities and options
# wxWidgets
find_package(wxWidgets)
IF(wxWidgets_FOUND)
  include("${wxWidgets_USE_FILE}")
ELSE(wxWidgets_FOUND)
  message(ERROR "Failed to find wxWidgets")
ENDIF(wxWidgets_FOUND)

############################################################
## libgpPanel
add_subdirectory(gpPanel)

############################################################
## install: headers
install(DIRECTORY include/  DESTINATION ${INSTALL_INCLUDEDIR}/gppanel/)

## install: docs
install(DIRECTORY gpPanel/docs/ DESTINATION ${INSTALL_DATADIR})
install(FILES
  gpPanel/licence.txt
  gpPanel/readme.txt
  gpPanel/MathplotMyModifications.txt
  DESTINATION ${INSTALL_DATADIR})

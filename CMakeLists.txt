cmake_minimum_required(VERSION 2.8)
project(kiss_platform)
include(ExternalProject)

set(PREFIX "${CMAKE_CURRENT_BINARY_DIR}")
set(INSTALL_DIR "${CMAKE_CURRENT_BINARY_DIR}")
set(CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${INSTALL_DIR})

ExternalProject_Add(opencv
  PREFIX ${PREFIX}
  GIT_REPOSITORY https://github.com/Itseez/opencv.git
  INSTALL_DIR ${INSTALL_DIR}
  CMAKE_ARGS ${CMAKE_ARGS}
)

ExternalProject_Add(libkar
  PREFIX ${PREFIX}
  GIT_REPOSITORY https://github.com/kipr/libkar.git
  INSTALL_DIR ${INSTALL_DIR}
  CMAKE_ARGS ${CMAKE_ARGS}
)

ExternalProject_Add(pcompiler
  PREFIX ${PREFIX}
  GIT_REPOSITORY https://github.com/kipr/pcompiler.git
  INSTALL_DIR ${INSTALL_DIR}
  CMAKE_ARGS ${CMAKE_ARGS}
)

ExternalProject_Add(libkovan
  PREFIX ${PREFIX}
  GIT_REPOSITORY https://github.com/kipr/libkovan.git
  INSTALL_DIR ${INSTALL_DIR}
  CMAKE_ARGS ${CMAKE_ARGS}
  DEPENDS opencv
)

ExternalProject_Add(kiss
  PREFIX ${PREFIX}
  GIT_REPOSITORY https://github.com/kipr/kiss.git
  INSTALL_DIR ${INSTALL_DIR}
  CMAKE_ARGS ${CMAKE_ARGS}
  DEPENDS libkar pcompiler
)

ExternalProject_Add(computer
  PREFIX ${PREFIX}
  GIT_REPOSITORY https://github.com/kipr/computer.git
  INSTALL_DIR ${INSTALL_DIR}
  CMAKE_ARGS ${CMAKE_ARGS}
  DEPENDS kiss libkovan
)
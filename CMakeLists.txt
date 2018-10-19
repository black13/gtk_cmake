# Set the name and the supported language of the project
PROJECT(hello-world C)
# Set the minimum version of cmake required to build this project
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

# Use the package PkgConfig to detect GTK+ headers/library files
FIND_PACKAGE(PkgConfig REQUIRED)
PKG_CHECK_MODULES(GTK3 REQUIRED gtk+-3.0)

# Setup CMake to use GTK+, tell the compiler where to look for headers
# and to the linker where to look for libraries
INCLUDE_DIRECTORIES(${GTK3_INCLUDE_DIRS})
LINK_DIRECTORIES(${GTK3_LIBRARY_DIRS})
include_directories(
  ${GSTREAMER_INCLUDE_DIRS}
  ${GSTREAMER-APP_INCLUDE_DIRS}
  ${GSTREAMER-AUDIO_INCLUDE_DIRS}
  ${GSTREAMER-PBUTILS_INCLUDE_DIRS}
  ${GSTREAMER-FFT_INCLUDE_DIRS}
  ${CMAKE_CURRENT_SOURCE_DIR}
)

link_directories(
  ${GSTREAMER_LIBRARY_DIRS}
  ${GSTREAMER-APP_LIBRARY_DIRS}
  ${GSTREAMER-AUDIO_LIBRARY_DIRS}
  ${GSTREAMER-PBUTILS_LIBRARY_DIRS}
  ${GSTREAMER-FFT_LIBRARY_DIRS}
)
# Add other flags to the compiler
ADD_DEFINITIONS(${GTK3_CFLAGS_OTHER})

# Add an executable compiled from hello.c
ADD_EXECUTABLE(hello hello.c)

# Link the target to the GTK+ libraries
TARGET_LINK_LIBRARIES(hello ${GTK3_LIBRARIES})

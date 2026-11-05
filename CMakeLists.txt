# kobento-desktop — rcviewer, the macOS / Linux desktop viewer, built on rcplayer from
# kobento-libs.
#
#   cmake -S . -B build && cmake --build build      →  build/viewer/rcviewer
#
# The engine is a sibling checkout: ../kobento-libs next to this repository, or
# -DKOBENTO_LIBS_DIR=/path/to/kobento-libs. The Compose desktop player (compose/) builds
# with Gradle on its own.

cmake_minimum_required(VERSION 3.20)
project(KobentoDesktop LANGUAGES C CXX)

if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
endif()

set(KOBENTO_LIBS_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../kobento-libs" CACHE PATH "kobento-libs checkout")
if(NOT EXISTS "${KOBENTO_LIBS_DIR}/CMakeLists.txt")
    message(FATAL_ERROR "kobento-libs not found at ${KOBENTO_LIBS_DIR}: check it out next to kobento-desktop, or pass -DKOBENTO_LIBS_DIR=…")
endif()
add_subdirectory("${KOBENTO_LIBS_DIR}" kobento-libs)

add_subdirectory(viewer)

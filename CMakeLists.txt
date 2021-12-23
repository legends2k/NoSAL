cmake_minimum_required(VERSION 3.14)

project(
    NoSAL
    VERSION 0.1.0
    DESCRIPTION "Header disableing SAL annotations (sal.h)"
    HOMEPAGE_URL "https://github.com/legends2k/nosal"
    LANGUAGES NONE
)

include(cmake/project-is-top-level.cmake)
include(cmake/variables.cmake)

# ---- Declare library ----

add_library(NoSAL_NoSAL INTERFACE)
add_library(NoSAL::NoSAL ALIAS NoSAL_NoSAL)

set_property(
    TARGET NoSAL_NoSAL PROPERTY
    EXPORT_NAME NoSAL
)

target_include_directories(
    NoSAL_NoSAL ${warning_guard}
    INTERFACE
    "$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>"
)

target_compile_features(NoSAL_NoSAL INTERFACE cxx_std_11)

# ---- Install rules ----

if(NOT CMAKE_SKIP_INSTALL_RULES)
  include(cmake/install-rules.cmake)
endif()

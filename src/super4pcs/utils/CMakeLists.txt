set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(utils_ROOT "${SRC_DIR}/utils")

find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIR})


#############################################

set(utils_INCLUDE
    ${utils_ROOT}/timer.h
    ${utils_ROOT}/geometry.h
    ${utils_ROOT}/disablewarnings.h)

# use library target, to make accessible to test routines
add_library(super4pcs_utils INTERFACE)
target_sources(super4pcs_utils INTERFACE ${utils_INCLUDE})

#
# HACK: have the files showing in the IDE, under the name 'super4pcs_utils_IDE'
# Source: https://stackoverflow.com/questions/27039019/how-to-have-cmake-show-headers-that-are-not-part-of-any-binary-target-in-the-ide/29214327#29214327
#
add_custom_target(super4pcs_utils_IDE SOURCES ${utils_INCLUDE})

cmake_minimum_required(VERSION 3.15...3.26)
project(${SKBUILD_PROJECT_NAME} VERSION ${SKBUILD_PROJECT_VERSION})


# Find CGAL library
find_package(CGAL CONFIG REQUIRED)

# pybind11
find_package(Python REQUIRED COMPONENTS Interpreter Development.Module)
find_package(pybind11 CONFIG REQUIRED)
# Add subdirectories for the bindings and module
add_subdirectory(trajgenpy_bindings)

install(
    DIRECTORY ${CMAKE_SOURCE_DIR}/dlls/
    DESTINATION ${SKBUILD_PLATLIB_DIR}
    FILES_MATCHING PATTERN "*.dll"
)

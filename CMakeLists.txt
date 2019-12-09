cmake_minimum_required(VERSION 2.8.12)

project(libbubbler_example)
enable_language(CXX)

# Tell CMAKE where the Findlibbubbler module lives
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR}/cmake)

# Locate libubbbler and set relevant variables
find_package(libbubbler REQUIRED)
add_definitions(${LIBBUBBLER_DEFINITIONS})
include_directories(${LIBBUBBLER_INCLUDE_DIRS})
set(LIBRARIES ${LIBRARIES} ${LIBBUBBLER_LIBRARIES})

# Build the executable, and give it access to the libbubbler includes / library
add_executable(gaussian src/gaussian_potential_test.cpp)
target_link_libraries(gaussian ${LIBRARIES})
target_include_directories(gaussian PUBLIC ${LIBBUBBLER_INCLUDE_DIRS})
set_target_properties(gaussian PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
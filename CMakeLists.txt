cmake_minimum_required(VERSION 3.24)

project(sfml_example LANGUAGES CXX)

# Download a CPM.cmake
file(
  DOWNLOAD
  https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.38.7/CPM.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
  EXPECTED_HASH SHA256=83e5eb71b2bbb8b1f2ad38f1950287a057624e385c238f6087f94cdfc44af9c5
)
include(${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake)

add_executable(${PROJECT_NAME} src/main.cpp)

set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 20)
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD_REQUIRED On)

set(BUILD_SHARED_LIBS FALSE)

CPMAddPackage("gh:SFML/SFML#2.6.1")

target_link_libraries(${PROJECT_NAME} sfml-graphics sfml-window sfml-system)

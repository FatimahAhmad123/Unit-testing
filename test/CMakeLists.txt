cmake_minimum_required(VERSION 3.12)

project(unitTest)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../external/googletest)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/../include
	${CMAKE_CURRENT_SOURCE_DIR}/../src
)

add_executable(tests test.cpp)

target_link_libraries(tests PRIVATE gtest_main)

include(GoogleTest)
gtest_discover_tests(tests)

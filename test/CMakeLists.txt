cmake_minimum_required(VERSION 3.12)

project(Test)

add_library(project_lib STATIC
	${CMAKE_CURRENT_SOURCE_DIR}/../src/student.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/../src/whitelist.cpp
)

set(GTEST_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../googletest)

add_subdirectory(${GTEST_DIR} ${CMAKE_CURRENT_BINARY_DIR}/googletest)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/../include
	${CMAKE_CURRENT_SOURCE_DIR}/../src
	${GTEST_DIR}/include
)
message(${GTEST_DIR}/include)

add_executable(tests test.cpp)

target_link_libraries(tests PRIVATE gtest_main project_lib pthread)

include(GoogleTest)
gtest_discover_tests(tests)
cmake_minimum_required(VERSION 3.9)
set(PROJECT_NAME "empty-project")
project(${PROJECT_NAME} VERSION 1.0)

set(CMAKE_CXX_STANDARD 11)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

set(SRC_MAIN
	main.cpp
	third_party/argtable3/argtable3.c
)

include_directories("third_party")

add_executable(empty-project ${SRC_MAIN})
target_link_libraries(empty-project PRIVATE
	${EXTRA_LIBS}
)

INSTALL(PROGRAMS ${CMAKE_CURRENT_BINARY_DIR}/empty-project DESTINATION cmake)
INSTALL(FILES README.md LICENSE HISTORY COPYING TODO CODE_OF_CONDUCT.md CONTRIBUTING.md DESTINATION doc)

include(InstallRequiredSystemLibraries)
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/LICENSE")
set(CPACK_PACKAGE_VERSION_MAJOR "1")
set(CPACK_PACKAGE_VERSION_MINOR "1")
include(CPack)

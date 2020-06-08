cmake_minimum_required(VERSION 3.16)
project(OpenGLFuns VERSION 0.1.1)

set(CMAKE_CXX_STANDARD 14)

include_directories( include )
include_directories(extern/glfw-3.0.4/include)

LINK_DIRECTORIES( ${CMAKE_SOURCE_DIR}/lib )

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)



find_package(OpenGL)

set (CMAKE_DEBUG_POSTFIX "_d")

set(RUN_DIR ${PROJECT_SOURCE_DIR}/bin)



add_executable(OpenGLFuns src/main.cpp)
set_property(TARGET OpenGLFuns PROPERTY DEBUG_POSTFIX _d)
target_link_libraries(OpenGLFuns optimized glfw3 debug glfw3_d ${GLFW_LIBRARIES} ${OPENGL_LIBRARIES})


ADD_CUSTOM_TARGET(debug ${CMAKE_COMMAND} -DCMAKE_BUILD_TYPE:STRING=Debug ${PROJECT_SOURCE_DIR})
ADD_CUSTOM_TARGET(release ${CMAKE_COMMAND} -DCMAKE_BUILD_TYPE:STRING=Release ${PROJECT_SOURCE_DIR})
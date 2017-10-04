# Copyright (c) 2017 Eduardo Costa
# 
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
cmake_minimum_required(VERSION 3.9)
project(opengl-headers VERSION 2017.01.03)

set(EXPORT_NAME "${PROJECT_NAME}-config")

add_library(${PROJECT_NAME} INTERFACE)
target_include_directories(${PROJECT_NAME} INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/api>
  $<INSTALL_INTERFACE:include>
)

if(APPLE)
    target_compile_definitions(${PROJECT_NAME} INTERFACE "GL_GLEXT_PROTOTYPES")
    target_link_libraries(${PROJECT_NAME} INTERFACE "-framework OpenGL")
endif()

install(TARGETS ${PROJECT_NAME} EXPORT ${EXPORT_NAME})
install(EXPORT ${EXPORT_NAME} DESTINATION "lib/cmake/${PROJECT_NAME}")
install(DIRECTORY api/ DESTINATION include)


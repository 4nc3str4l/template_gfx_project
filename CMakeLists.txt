cmake_minimum_required(VERSION 3.10) 

project(template_gfx_project)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)


############################################################
#                         GLAD                             #
############################################################

set(GLAD_DIR ${CMAKE_SOURCE_DIR}/libs/glad)
set(GLAD_SOURCES ${GLAD_DIR}/src/glad.c)
set(GLAD_INCLUDE_DIR ${GLAD_DIR}/include)

include_directories(${GLAD_INCLUDE_DIR})

add_executable(template_gfx_project 
    main.cpp
    ${GLAD_SOURCES}
)

if(UNIX AND NOT APPLE)
    target_link_libraries(template_gfx_project dl)
endif()


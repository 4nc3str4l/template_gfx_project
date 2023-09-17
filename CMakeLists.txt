cmake_minimum_required(VERSION 3.10) 

project(template_gfx_project)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

############################################################
#                         SDL2                             #
############################################################
set(SDL2_DIR "${CMAKE_SOURCE_DIR}/libs/SDL2")
set(SDL2_INCLUDE_DIRS "${SDL2_DIR}/include")

if(${CMAKE_SIZEOF_VOID_P} EQUAL 8)
    # 64 bits
    set(SDL2_DLL "${SDL2_DIR}/lib/x64/SDL2.dll")
    set(SDL2_LIBRARY_DIR "${SDL2_DIR}/lib/x64")
else()
    # 32 bits
    set(SDL2_DLL "${SDL2_DIR}/lib/x86/SDL2.dll")
    set(SDL2_LIBRARY_DIR "${SDL2_DIR}/lib/x86")
endif()

link_directories(${SDL2_LIBRARY_DIR})
include_directories(${SDL2_INCLUDE_DIRS} include libs)

############################################################
#                         GLAD                             #
############################################################

set(GLAD_DIR ${CMAKE_SOURCE_DIR}/libs/glad)
set(GLAD_SOURCES ${GLAD_DIR}/glad.c)
set(GLAD_INCLUDE_DIR ${GLAD_DIR})

include_directories(${GLAD_INCLUDE_DIR})

############################################################
#                         IMGUI                            #
############################################################
file(GLOB IMGUI_SOURCES ${CMAKE_SOURCE_DIR}/libs/imgui/*.cpp)
file(GLOB IMGUI_HEADERS ${CMAKE_SOURCE_DIR}/libs/imgui/*.h)


############################################################
#                         EXECUTABLE                       #
############################################################

add_executable(template_gfx_project 
    main.cpp
    ${GLAD_SOURCES}
    ${IMGUI_SOURCES}
    ${IMGUI_HEADERS}
)

############################################################
#                         LINKING                          #
############################################################
target_link_libraries(template_gfx_project ${SDL2_LIBRARIES} SDL2main SDL2)

############################################################
#                         COPY DLL                         #
############################################################
if(WIN32)
    set_target_properties(template_gfx_project PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}/build")

    add_custom_command(TARGET template_gfx_project POST_BUILD COMMAND
        ${CMAKE_COMMAND} -E copy_if_different
        ${SDL2_DLL}
        $<TARGET_FILE_DIR:template_gfx_project>
    )
endif()

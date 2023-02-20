cmake_minimum_required(VERSION 3.21)

project(imgui)

message("-- ${PROJECT_NAME} : static")

find_package(PkgConfig REQUIRED)
find_package(OpenGL REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

add_library(${PROJECT_NAME} STATIC)

target_sources(
    ${PROJECT_NAME}
    PRIVATE
        imgui.cpp
        imgui_demo.cpp
        imgui_draw.cpp
        imgui_tables.cpp
        imgui_widgets.cpp

        backends/imgui_impl_glfw.cpp
        backends/imgui_impl_opengl3.cpp
)

target_include_directories(
    ${PROJECT_NAME}
    PUBLIC .
)

target_link_libraries(
    ${PROJECT_NAME}
    ${GLFW_LIBRARIES}
    ${OPENGL_LIBRARIES}
)

cmake_minimum_required(VERSION 3.5)
project(ui_dig CXX)

find_package(OpenGL REQUIRED)

include_directories( include external/imgui ${OPENGL_INCLUDE_DIR} )

add_executable(ui_dig
    src/main.cpp
    external/imgui/imgui.cpp
    external/imgui/imgui_widgets.cpp
    external/imgui/imgui_tables.cpp
    external/imgui/imgui_draw.cpp
    external/imgui/imgui_demo.cpp
    external/imgui/backends/imgui_impl_opengl3.cpp
    external/imgui/backends/imgui_impl_win32.cpp
    )

if (WIN32)
    SET (LIBS dwmapi ${OPENGL_LIBRARIES})
else() 
    SET(LIBS ${OPENGL_LIBRARIES})
endif (WIN32)

target_link_libraries(ui_dig ${LIBS})
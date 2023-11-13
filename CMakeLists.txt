cmake_minimum_required(VERSION 3.5)
project(ui_dig CXX)

include_directories( include external/imgui )

add_executable(ui_dig
    src/main.cpp
    external/imgui/imgui.cpp
    external/imgui/imgui_widgets.cpp
    external/imgui/imgui_tables.cpp
    external/imgui/imgui_draw.cpp
    external/imgui/imgui_demo.cpp
    external/imgui/backends/imgui_impl_dx11.cpp
    external/imgui/backends/imgui_impl_win32.cpp
    )

# даёт успешную линковку на w10
target_link_libraries(ui_dig dwmapi d3d11 d3dcompiler)
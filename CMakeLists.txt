cmake_minimum_required(VERSION 3.21)
project(ui_dig CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON) 

find_package(OpenGL REQUIRED)
find_package(SDL2 REQUIRED)

include_directories( include external/imgui ${OPENGL_INCLUDE_DIR} ${SDL2_INCLUDE_DIR} )

add_executable(ui_dig
    src/main.cpp
    external/imgui/imgui.cpp
    external/imgui/imgui_widgets.cpp
    external/imgui/imgui_tables.cpp
    external/imgui/imgui_draw.cpp
    external/imgui/imgui_demo.cpp
    external/imgui/backends/imgui_impl_opengl3.cpp
    external/imgui/backends/imgui_impl_sdl2.cpp
    )

target_link_libraries(ui_dig ${OPENGL_LIBRARIES} ${SDL2_LIBRARIES} "-mwindows")
# -mwindows suppresses terminal output

# 2 in https://stackoverflow.com/a/75065206 (dlls from msys)
install(TARGETS ui_dig
    RUNTIME ARCHIVE LIBRARY RUNTIME FRAMEWORK BUNDLE PUBLIC_HEADER RESOURCE)
install(TARGETS ui_dig
    COMPONENT ui_dig
    RUNTIME_DEPENDENCIES
    PRE_EXCLUDE_REGEXES "api-ms-" "ext-ms-"
    POST_EXCLUDE_REGEXES ".*system32/.*\\.dll"
    DIRECTORIES $<TARGET_FILE_DIR:ui_dig> "C:\\msys64\\mingw64\\bin" )

# https://cmake.org/cmake/help/book/mastering-cmake/chapter/Packaging%20With%20CPack.html
set(CPACK_PACKAGE_NAME "ui_dig")
set(CPACK_PACKAGE_VENDOR "me")
set(CPACK_PACKAGE_VERSION "0.1.2")
set(CPACK_PACKAGE_VERSION_MAJOR "0")
set(CPACK_PACKAGE_VERSION_MINOR "1")
set(CPACK_PACKAGE_VERSION_PATCH "2")

set (CPACK_CREATE_DESKTOP_LINKS ui_dig)
set (CPACK_PACKAGE_EXECUTABLES "ui_dig" "UI DIG" )


set (CPACK_RESOURCE_FILE_LICENSE
     "${CMAKE_CURRENT_SOURCE_DIR}/nolicense.txt")
include(CPack)
# ui_dig
Сделано на windows из https://github.com/ocornut/imgui/blob/master/examples/example_sdl2_opengl3/main.cpp
```shell
# добавить C:\msys64\mingw64\bin в PATH
# pacman -Sy mingw-w64-x86_64-ninja mingw-w64-x86_64-gcc mingw-w64-x86_64-cmake mingw-w64-x86_64-SDL2
# либо build-essential libsdl2-dev в debian(-based)
git clone --recursive https://github.com/alexanderustinov/ui_dig.git
mkdir build ; cd build
cmake ../
ninja
```

## Установщик
```shell
# pacman -Sy mingw-w64-x86_64-nsis
cd build
ninja package
# .\ui_dig-0.1.2-win64.exe
```
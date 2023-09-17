# template_gfx_project

`template_gfx_project` serves as a foundational project designed for seamless integration of OpenGL and ImGui. Its primary objective is to offer a boilerplate codebase for developers looking to initiate a graphical application harnessing OpenGL for rendering and ImGui for graphical user interfaces.

While it's feasible to structure this as a library, allowing users to simply embed logic within `Update()`, `Render()`, and `RenderIMGUI()` functions, that is not the intent of this project. The primary goal is to ensure everything is set up and operational whenever I wish to create a new application utilizing these libraries as I allways find myself loosing 1h to setup everything.

![Project Image](./github/picture.PNG)

## Dependencies

The project relies on the following libraries:

- **[glad](https://glad.dav1d.de/):** Provides the source code to handle OpenGL function pointers.
- **[SDL2](https://github.com/libsdl-org/SDL):** Used for creating a window, OpenGL context, and handling input.
- **[ImGui](https://github.com/ocornut/imgui):** An immediate-mode GUI library to create interfaces within the OpenGL context.

## Building the Project

The project uses CMake as its build system. Here are the steps to compile the project:
```sh
mkdir build
cd build
cmake ..
cmake --build .
```
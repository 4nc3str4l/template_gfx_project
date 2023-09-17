# template_gfx_project

`template_gfx_project` is a foundational project set up to facilitate OpenGL and ImGui integration. The purpose of this project is to provide a boilerplate codebase for developers who want to start a graphical application with the capabilities of OpenGL for rendering and ImGui for graphical user interfaces.

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
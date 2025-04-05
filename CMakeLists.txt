cmake_minimum_required(VERSION 3.10)
project(ImGuiGLFWTemplate)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Path to ImGui and GLFW
set(IMGUI_DIR "${CMAKE_SOURCE_DIR}/imgui")
set(GLFW_DIR "${CMAKE_SOURCE_DIR}/libs/glfw")

# Add GLFW subdirectory
add_subdirectory(${GLFW_DIR} glfw_build)

# Add ImGui source files
file(GLOB IMGUI_SRC
    ${IMGUI_DIR}/*.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
)

# Create executable
add_executable(main main.cpp ${IMGUI_SRC})

# Include directories for ImGui and GLFW
target_include_directories(main PRIVATE ${IMGUI_DIR} ${IMGUI_DIR}/backends)

# Link OpenGL, GLFW, and ImGui
target_link_libraries(main PRIVATE glfw OpenGL::GL)

# macOS specific linking
if(APPLE)
    target_link_libraries(main PRIVATE "-framework Cocoa" "-framework OpenGL" "-framework IOKit" "-framework CoreVideo")
endif()

# Find OpenGL
find_package(OpenGL REQUIRED)

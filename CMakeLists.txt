
cmake_minimum_required(VERSION 3.10)
project(ImGuiGLFWTemplate)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(IMGUI_DIR "Path to imgui" "${CMAKE_SOURCE_DIR}/imgui")
option(GLFW_DIR "Path to glfw" "${CMAKE_SOURCE_DIR}/libs/glfw")

add_subdirectory(${GLFW_DIR} glfw_build)

file(GLOB IMGUI_SRC
    ${IMGUI_DIR}/*.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
)

add_library(imgui STATIC ${IMGUI_SRC})
target_include_directories(imgui PUBLIC
    ${IMGUI_DIR}
    ${IMGUI_DIR}/backends
)
target_link_libraries(imgui PUBLIC glfw)

add_executable(main main.cpp)
target_include_directories(main PRIVATE ${IMGUI_DIR} ${IMGUI_DIR}/backends)
target_link_libraries(main PRIVATE imgui glfw OpenGL::GL)

find_package(OpenGL REQUIRED)

if(APPLE)
    target_link_libraries(main PRIVATE "-framework Cocoa" "-framework OpenGL" "-framework IOKit" "-framework CoreVideo")
endif()

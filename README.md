
# ImGui + GLFW C++ Starter Template

This is a lightweight, cross-platform C++ starter template integrating [Dear ImGui](https://github.com/ocornut/imgui) with [GLFW](https://github.com/glfw/glfw) using OpenGL and CMake.

## 🧰 Features

- 📦 Minimal dependencies
- 🖼️ Dear ImGui UI rendering
- 🎮 GLFW for window/context/input
- 💡 OpenGL for graphics backend
- 📋 CMake build system
- 💻 Cross-platform: Windows, macOS, Linux

---

## 🚀 Quick Start

### 1. Clone the Repo

```bash
git clone https://github.com/YOUR_USERNAME/imgui-glfw-template.git
cd imgui-glfw-template
```

### 2. Add Dependencies

#### Option A: As Submodules

```bash
git submodule update --init --recursive
```

#### Option B: Manual

- Download and extract [Dear ImGui](https://github.com/ocornut/imgui) into `imgui/`
- Download and extract [GLFW](https://github.com/glfw/glfw) into `libs/glfw/`

### 3. Build

```bash
mkdir build
cd build
cmake ..
cmake --build .
```

### 4. Run

```bash
./main   # or main.exe on Windows
```

---

## 📁 Structure

```
.
├── main.cpp
├── CMakeLists.txt
├── imgui/            # Dear ImGui source
└── libs/
    └── glfw/         # GLFW source
```

---

## 🧱 Dependencies

- C++17
- OpenGL
- CMake ≥ 3.10

---

## 📝 License

This template itself is MIT licensed. See [Dear ImGui](https://github.com/ocornut/imgui) and [GLFW](https://github.com/glfw/glfw) for their licenses.

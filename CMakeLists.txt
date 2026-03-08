cmake_minimum_required(VERSION 3.10)
project(ThreeBodySim)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find CUDA
find_package(CUDA REQUIRED)

# Add the executable
add_executable(ThreeBodySim
    main.cpp
    src/Body.cpp
    src/Simulation.cpp
    src/Renderer.cpp
    src/cuda/kernel.cu
)

# Include directories
include_directories(${CUDA_INCLUDE_DIRS})
include_directories(src)
include_directories(src/cuda)

# Link CUDA
target_link_libraries(ThreeBodySim CUDA::cuda)

# Optional: Link GLFW and GLAD (you may need to install them via apt)
# find_package(GLFW REQUIRED)
# find_package(GLAD REQUIRED)
# target_link_libraries(ThreeBodySim GLFW::GLFW GLAD::GLAD)
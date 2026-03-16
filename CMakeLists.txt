cmake_minimum_required(VERSION 3.15)

project(3D_stenosed_artery)

# Find IBAMR
find_package(IBAMR 0.18.0 REQUIRED)

# Create executable
add_executable(3D_stenosed_artery main.cpp)

# Link IBAMR (3D version)
target_link_libraries(3D_stenosed_artery IBAMR::IBAMR3d)

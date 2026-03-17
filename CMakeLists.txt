cmake_minimum_required(VERSION 3.16)

project(3D_stenosed_artery)

find_package(MPI REQUIRED)
find_package(IBAMR REQUIRED)

include_directories(
/home/divyasingh/autoibamr/packages/IBAMR-0.18.0/include
/home/divyasingh/autoibamr/packages/IBSAMRAI2-2025.10.29/include
/home/divyasingh/autoibamr/packages/petsc-3.23.3/include
/home/divyasingh/autoibamr/packages/petsc-3.23.3/arch-linux-c-opt/include
/home/divyasingh/autoibamr/packages/libmesh-1.7.8/include
/home/divyasingh/autoibamr/packages/hdf5-1.12.2/include
/usr/local/include
/usr/include/eigen3
${MPI_INCLUDE_PATH}
)

add_executable(3D_stenosed_artery artery.cpp)

target_link_directories(3D_stenosed_artery PRIVATE
/home/divyasingh/autoibamr/packages/IBAMR-0.18.0/lib
/home/divyasingh/autoibamr/packages/libmesh-1.7.8/lib 
/home/divyasingh/autoibamr/packages/petsc-3.23.3/arch-linux-c-opt/lib
/home/divyasingh/autoibamr/packages/hdf5-1.12.2/lib
/home/divyasingh/autoibamr/packages/parmetis-4.0.3/lib
/home/divyasingh/autoibamr/packages/IBSAMRAI2-2025.10.29/lib
)

set_target_properties(3D_stenosed_artery PROPERTIES
BUILD_RPATH "/home/divyasingh/autoibamr/packages/IBAMR-0.18.0/lib;
/home/divyasingh/autoibamr/packages/petsc-3.23.3/arch-linux-c-opt/lib;
/home/divyasingh/autoibamr/packages/hdf5-1.12.2/lib"
)

target_link_libraries(
3D_stenosed_artery

# IBAMR
IBAMR3d
IBTK3d

# libMesh
mesh_opt
timpi_opt

# SAMRAI
SAMRAI2d
SAMRAI3d

# Core dependencies
petsc
HYPRE
hdf5

# MPI
MPI::MPI_C
MPI::MPI_CXX
)

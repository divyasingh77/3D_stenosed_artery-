
##################################################
git clone https://github.com/divyasingh77/3D_stenosed_artery-.git
cd 3D_stenosed_artery-

Create a build directory:
rm -rf build
mkdir build
cd build

Set PETSc environment variables:
export PETSC_DIR=/home/divyasingh/autoibamr/packages/petsc-3.23.3
export PETSC_ARCH=arch-linux-c-opt

Configure using CMake:
cmake -DIBAMR_DIR=/home/divyasingh/autoibamr/packages/IBAMR-0.18.0/lib/cmake/ibamr ..

Compile the code:
make -j4

Run using MPI:
mpirun -np 4 ./3D_stenosed_artery ../input3d

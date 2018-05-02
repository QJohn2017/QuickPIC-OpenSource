# ![QUICKPIC](http://exodus.physics.ucla.edu/~uclapic/repo_images/quickpic.png)
QuickPIC is a 3D parallel (MPI & OpenMP Hybrid) Quasi-Static PIC code, which is developed based on the framework UPIC. This is the UCLA Plasma Simulation Group's official open-source repository for QuickPIC.

## Branch: Cori-Vec

In addition to the MPI-OpenMP hybrid algorithm, this branch contains new 2D particle subroutines (in source/part2d_lib77.f) using vectorization algorithm. The vectorization algorithm is originally from [UPIC Skeleton Code](https://picksc.idre.ucla.edu/software/skeleton-code/). The algorithm in current code is transformed from the original one to one that solves the Quasi-Static-Approximation PIC model. It also has been modified to enable MPI. A simple profiling tool is added in the code to show the computing time consumed on the interested procedures. The code can be compiled and run on Cori at [NERSC](http://nersc.gov/).

# Upon cloning the repository

If you clone this repository, we ask that you __please contact__ Weiming An (anweiming@ucla.edu). The development of QuickPIC relies on grant funding for which we are required to report code usage, and we would greatly appreciate being able to maintain accurate user-number tallies.

Please also feel free to send an email to this address if you would like assistance using the code, if you have any questions related to the code base, or if you have suggestions for improvements. We are in the process of establishing a user forum for discussions related to the use and development of QuickPIC and will be more than happy to include you in such a forum if you desire.

# Compile QuickPIC

The makefile is set to use gcc and gfortran with MPI. HDF5-Parallel is also required
for compiling. 

To compile the programs, execute:

make

The program name is qpic.e

The command to execute a program with both MPI and OpenMP varies from
one system to another.  One possible command is:

mpirun -np nproc ./qpic.e

where nproc is the number of processors to be used.

By default, OpenMP will use the maximum number of processors it can find
on the MPI node.  If the user wants to control the number of threads, the
environment variable 'OMP_NUM_THREADS' may need to be set to the maximum
number of threads per node expected.

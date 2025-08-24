I spent these two weeks mainly by optimising and refactoring the code. Currently, the code was computing constant values such as cell areas in each iteration, which was memory efficient, but computationally extremely inefficient. Also, for the majority of the computations, each kernel bound to a specific cell needed information from the adjacent cells, and the search for these cell neighbors was performed for every cell in every iteration. 

I solved this problem by pre-computing most of the constant data, such as cell area, cell geometry for computing the time steps and generating vectors of cell indices. 

When evaluating the boundary condition, the ghost cell takes data from the adjacent inner cell. At first, the kernel would search for all neighboring cells and check each cell neighbor's cell ID and thus determining the ghost cell's inner cell neighbor. The new approach did this once before the main iteration loop would begin and store the results in a vector, from which the kernel could reference the inner cell index. 

For evaluating the fluxes in the main computational domain, a similar approach was chosen. Each inner cell has four neighbors and four interfaces, which would previously be searched for. Now, their indices are stored in a static vector unique for each inner cell. 

In doing so, it became clear that the main bottleneck for the speed of my code was accessing the Mesh data structure. By precomputing all the necessary data, the kernels would no longer need to reference this object and the code became as fast as my bachelor's thesis on processors and even faster on a GPU. The speedup on GPU was roughly 200x. 

I ended this time period by refactoring the code so that there is a Simulation object with parameters const MeshData and non-const FluidData. This way, I didn't need to pass so many parameters as arguments of functions and thus I made the code a lot more readable. 
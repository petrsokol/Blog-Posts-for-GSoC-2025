In these two weeks, I continued my work on rewriting my code from my bachelor's thesis to work with TNL. 

I started by creating vectors of data where every index corresponded to one cell and then filling these vectors by initial conditions. I also implemented the different boundary condition types for walls, inlet and outlet. 

I continued by implementing a function to calculate the size of a time step for every cell based on its geometry and flow velocity. These values would be also stored in another vector to be later accessed by the solver. 

At the ent of these two weeks, I have successfully rewritten the basic Euler equation solver for 2D from my bachelor's thesis. The results seem to match, since both the bachelor's thesis and this implementation converge to the same numerical results. However, I still didn't know how to export the data in a way that I could visualise them in paraView to further confirm their validity. 
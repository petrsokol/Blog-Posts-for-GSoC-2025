During weeks 28 and 29 of 2025, the HLLC scheme was added. 

The results could now also be exported in a .vtk file format, so scalar fields such as the Mach number or the pressure coefficient could be visualised in software like ParaView. 

I also started to clean up the code and divide it into multiple .h files for clarity, which helped a lot with the code readability. 

I was also able to run the code on the CUDA device as well, but it was very slow for reasons which were not clear to me at the time. 

Finally, I added benchmarking, so I could see how long it takes to complete different procedures in my code. 
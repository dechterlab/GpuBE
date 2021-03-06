
# GpuBE
This code implements an inference-based algorithm which exploits Graphical Processing Units (GPUs) to speed up the resolution of exact and approximated inference-based algorithms for discrete optimization (e.g., WCSPs)
For details, please refer to the original paper:

Ferdinando Fioretto, Enrico Pontelli, William Yeoh, and Rina Dechter
[Accelerating Exact and Approximate Inference for (Distributed) Discrete Optimization with GPUs](https://arxiv.org/abs/1608.05288), CoRR abs/1608.05288 (2016). 

<!-- Ferdinando Fioretto, Tiep Le, Enrico Pontelli, William Yeoh, Tran Cao Son
[Exploiting GPUs in Solving (Distributed) Constraint Optimization Problems with Dynamic Programming](http://link.springer.com/chapter/10.1007%2F978-3-319-23219-5_9), In proceeding of CP 2015. -->

Compiling:
------------
GpuBE has been tested on MAC-OS-X and Linux operating systems. Prior compiling, you need to set up the following parameters in the Makefile:

	DEVICE_CC		(The device compute capability of the GPU)
	CUDA_PATH   	(The path to the CUDA libraries) 
	cudaDBE_PATH	(The path to GpuBE)

Then, from the GpuBE folder execute:

	make 

Executing:
------------
To execute GpuBE you need to specify a file format (currently [xcsp](http://arxiv.org/pdf/0902.2362v1.pdf) and [wcps](http://graphmod.ics.uci.edu/group/WCSP_file_format) formats are supported) and a solver [Bucket Elimination](http://www.sciencedirect.com/science/article/pii/S0004370299000594) or [MiniBucket Elimination](http://dl.acm.org/citation.cfm?id=1622343):

	gpuBE
	--format=[xml|wcsp] inputFile
	--agt=[cpuBE|gpuBE|cpuMiniBE z|gpuMiniBE z]
		where z is the maximal size of the mini-bucket
	Optional Parameters:
	[--root=X]      : The agent with id=X is set to be the root of the pseudoTree
	[--heur={0,1,2,3,4,5}] : The PseudoTree construction will use heuristic=X
		where 0 = ascending order based on the variables' ID
			  1 = descending order based on the variables' ID
			  2 = ascending order based on the number of neighbors of a variables
			  3 = descending order based on the number of neighbors of a variables
			  4 = ascending order based on the variables' name (lexicographic order)
			  5 = descending order based on the variables' name (lexicographic order)
	[--max[MB|GB=X]: X is the maximum amount of memory used by the GPU

Example:

	cudaBE --format=wcsp test/8queens.wcsp --agt=gpuMiniBE 8


## Contacts
fioretto@umich.edu 

Ferdinando Fioretto

Department of Industrial and Operations Engineering<br>
University of Michigan<br>
G827 IOE<br>
Ann Arbor, MI 48109 - U.S.A.


## References
Ferdinando Fioretto, Enrico Pontelli, William Yeoh, and Rina Dechter
[Accelerating Exact and Approximate Inference for (Distributed) Discrete Optimization with GPUs](https://arxiv.org/abs/1608.05288), CoRR abs/1608.05288 (2016). 

Ferdinando Fioretto, Tiep Le, Enrico Pontelli, William Yeoh, Tran Cao Son
[Exploiting GPUs in Solving (Distributed) Constraint Optimization Problems with Dynamic Programming](http://link.springer.com/chapter/10.1007%2F978-3-319-23219-5_9), In proceedings of the _International Conference of Principles and Practice of Constraint Programming (CP)_, 2015.

Ferdinando Fioretto, William Yeoh and Enrico Pontelli
[A Dynamic Programming-Based MCMC Framework for Solving DCOPs with GPUs](http://link.springer.com/chapter/10.1007%2F978-3-319-44953-1_51). In proceedings of the _International Conference of Principles and Practice of Constraint Programming (CP)_, 2016.

Ferdinando Fioretto, William Yeoh and Enrico Pontelli. 
[Multi-Variable Agent Decomposition for DCOPs](http://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/12093). 
In Proceedings of the _AAAI Conference on Artificial Intelligence (AAAI)_, 2016. 

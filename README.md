# Accelerating Ultrasound Elasticity Imaging with a CUDA-MATLAB Approach
# Prerequesites

## Prerequisites to Run Demo
1. There are two options to execute the project code. 1) On GPU with MATLAB 2) Directly on the GPU

## Steps to Run MATLAB Demo
1. Clone the code repository `./Demo_MATLAB` and download the files to a local directory. 
2. Demo_MATLAB contains a compiled MEX binary `Corr2GPUMex_Final.mexa64` which is called in `main.m` for displacement estimation. The MEX was compiled for a 64-bit Linux OS. 
3. If neccessary, the MEX can be recompiled using the following two lines: 
```
   > nvcc -O0 -std=c++11 -c normXcorr_Host_Mex_Final.cu -Xcompiler -fPIC -I/usr/local/MATLAB/R2013a/extern/include;
   > mex Corr2GPUMex_Final.cpp normXcorr_Host_Mex_Final.o -lcudart -L"/local/linux/cuda"
```
4. Run `main.m` in MATLAB. `main.m` will load two pre/post frames of ultrasound images and perform the displacement estimation using the GPU code.  
5. Sample Output: 
======>>>>> For a Windows system...
   
## Steps to Run CUDA Demo
0. A C demo is also included in case the system doesn't have MATLAB support. 
1. Clone the code repository `./Demo_C` and download the files to a local directory. `Demo_C` contains the neccessary input files. 
2. `Demo_C` contains a precompiled binary `normXcorr2_FC` which can be executed using the following syntax: 
```
   > ./normXcorr2_FC 244 6224 244 6224 17 49 9 161 220 75
```

The input arguments associated with the execution call are: 
 * Width of pre image
 * Height of pre image
 * Width of post image
 * Height of post image
 * Shift in X direction
 * Shift in Y direction
 * Kernel width
 * Kernel height
 * Number of displacement points in X direction
 * Number of displacement points in Y direction
3. `Demo_C` also contains a Makefile which can be used to recompile the code, if neccessary. 



## Example
### CODE
![Image of CODE_1](https://github.com/mturney2/Final-Project-Code/blob/master/DEMO/FILE_1.png)
![Image of CODE_2](https://github.com/mturney2/Final-Project-Code/blob/master/DEMO/FILE_2.png)
![Image of CODE_3](https://github.com/mturney2/Final-Project-Code/blob/master/DEMO/FILE_3.png)
![Image of CODE_4](https://github.com/mturney2/Final-Project-Code/blob/master/DEMO/FILE_4.png)

### MATLAB OUTPUT
![Image of RESULT](https://github.com/mturney2/Final-Project-Code/blob/master/DEMO/OUTPUT.png)

### IMAGE COMPARISON
![Image of IMG_RESULT](https://github.com/mturney2/Final-Project-Code/blob/master/DEMO/resultppt.png)

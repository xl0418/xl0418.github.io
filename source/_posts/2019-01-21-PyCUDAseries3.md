---
title: "PyCUDA series 3: matrix multiplication using multiple blocks"
categories: [Research,GPU programming,pyCUDA]
tags: [Python, CUDA, GPU programming, Parallel computation]
---

A simple practice on matrix multiplication is shown in this post. The matrix product function can use multiple blocks to calculate multiplications of two matrix. 

<!--more-->
 
# A simple matrix multiplication

The most important part is the kernel function, which is given below

```Python
kernel_code_template = """
__global__ void matrixmulti(float *a, float *b, float *c)
{

    // 2D Thread ID 
    int tx = blockDim.x*blockIdx.x + threadIdx.x; // Compute column index
    int ty = blockDim.y*blockIdx.y + threadIdx.y; // Compute row index

    // Each thread loads one row of M and one column of N, 
    //   to produce one element of P.
    if((ty <%(MATRIX_SIZE)s) && (tx < %(MATRIX_SIZE)s))
    {
    // Pvalue is used to store the element of the matrix
    // that is computed by the thread
    float Pvalue = 0;
    for(int k=0; k<%(MATRIX_SIZE)s;++k)
    {
    float Aelement = a[ty*%(MATRIX_SIZE)s +k];
    float Belement = b[k*%(MATRIX_SIZE)s +tx];
    Pvalue += Aelement * Belement;
    }
    c[ty * %(MATRIX_SIZE)s + tx] = Pvalue;
    }

}
"""

```

Note that the evaluation of C should be put in the conditional loop to guarentee that over-requested threads would not be invoked. 


# An odd bug

The code works well when the matrix size is less than 320\*320 and requesting block size to be 32\*32. But when the matrix size exceeds 320, like 321, the matrix product produced by GPU is not equal to the result by CPU. The difference between them is very tiny, like the scale of 1e-5. So far, I don't quite understand where this bug comes from. Probabily it is due to the limit of the number of blocks in one grid? 



# Full code
It contains the example code and the speed test. Clone it [here](https://github.com/xl0418/GPU_Python/blob/master/gpu_matrixmultiplication.py)

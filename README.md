# Triton

This is the development repository of Triton, a language and compiler for writing highly efficient custom Deep-Learning primitives. The aim of Triton is to provide an open-source environment to write fast code at higher productivity than CUDA, but also with much higher flexibility than [TVM](https://github.com/apache/incubator-tvm) and without having to manually specify compute schedules.

The main components of Triton at the moment are:

- **Triton-C**: An imperative, single-threaded language for writing highly efficient compute-kernels at a relatively high abstraction level (think numpy-like array operations in a C-like language).
- **Triton-IR**: A special-purpose intermediate representation (Triton-IR) for aiding array-level program analysis and optimizations in Triton-C programs.
- **Triton-JIT**: An optimizing just-in-time compiler for Triton-IR, which generates GPU code on par with state-of-the-art CUDA-C  (e.g.,  [CUTLASS](https://github.com/NVIDIA/cutlass)). This includes transparent support for mixed-precision and Tensor Cores.

Bindings for **automatic** PyTorch custom op generations are included in  **PyTriton**, along with a small DSL based on einsum that supports convolutions, shift-convolutions, direct einsums, etc.

The formal foundations of this project are described in the following MAPL2019 publication: [Triton: An Intermediate Language and Compiler for Tiled Neural Network Computations](http://www.eecs.harvard.edu/~htk/publication/2019-mapl-tillet-kung-cox.pdf). Please cite us if you use our work!



## Installation

Triton is a fairly self-contained package and uses its own parser (forked from [wgtcc](https://github.com/wgtdkp/wgtcc)) and LLVM-8.0+ for code generation. 


```
sudo apt-get install llvm-8-dev
 pip install -e "git+https://github.com/ptillet/triton.git#egg=triton&subdirectory=python"
```


## Getting Started

Please visit the [documentation](https://docs.triton-lang.org) to get started with Triton


## Contributing

Please keep in mind that this is a project I have been carrying out completely on my own as part of my Ph.D. thesis. While I am confident in the approach, there are still many things to fix and to polish. Please contact me (ptillet AT g.harvard.edu) or raise an issue if you want to contribute!

## ISAAC (deprecated) for fast inference

Before working on Triton, I wrote custom auto-tuned PTX code for fast, quantized inference on GPUs. While this project is now deprecated, you can use it at your own risk by checking out the "isaac" tag in this repository.
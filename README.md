# BandMatrices.jl

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://jl-pkgs.github.io/BandMatrices.jl/dev)
[![CI](https://github.com/jl-pkgs/BandMatrices.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/jl-pkgs/BandMatrices.jl/actions/workflows/CI.yml)
[![Codecov](https://codecov.io/gh/jl-pkgs/BandMatrices.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/jl-pkgs/BandMatrices.jl)

> 不依赖与任何包的的带状矩阵算法库, 为了后期将代码移植到GEE。   
> A band matrix algrithm library, which doesn't rely on any other packages, for later porting to GEE to speed up matrix solving.

## Band Matrix Storage

- `lapack`
  `A[i, j] => B[j, i - j + q + 1]`

- `kong`
  `A[i, j] => B[i, j - i + p + 1]`

- $p$: 下行带宽 (lower binwidth)
- $q$: 上行带宽 (upper binwidth)
- $A$: 原始带状矩阵 (Matrix, or Band Matrix)
- $B$: 压缩后的带状矩阵 (Banded Matrix)

> Julia有一种更简洁的代码设计方式，通过修改修改`getindex`和`setindex`方式。
> 但GEE不支持函数重载，因此暂时没有实现这种方式。

## See also

1. `BandedMatrices.jl`, <https://github.com/JuliaLinearAlgebra/BandedMatrices.jl>

2. Band Matrix Storage, <https://www.netlib.org/lapack/lug/node124.html>

3. The Algorithm of Doolittle's Method for LU Decompositions, <http://mathonline.wikidot.com/the-algorithm-for-doolittle-s-method-for-lu-decompositions>

4. 矩阵计算（二）：带状矩阵结构、效率及存储，<https://zhuanlan.zhihu.com/p/400460201>

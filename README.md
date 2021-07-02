# Requirements

**Python 3.8+**

**Python modules**:
- numpy
- matplotlib
- tqdm

# Youtube video

<ins>**https://youtu.be/nwAKu01ESlY**</ins>

# Description
`viz.ipynb` contains all the code necessary to generate the animations shown in the video.

# Fourier Transform with arbitrary basis

Let's say we have a signal $` x `$ with samples $` x_0, \ldots, x_{N-1} \in \mathbb{C} `$. The Discrete Time Fourier Transform (DTFT) finds coefficients $` X_k `$ such that:
```math
x_n = \frac1N\sum_{k=0}^{N-1} X_k e^{i2\pi kn/N} \quad  n=0, \ldots, N-1
```


We want to replace $` e^{i2\pi kn/N} `$ with an arbitrary function $` y `$ with samples $` y_0, \ldots, y_{N-1} \in \mathbb{C} `$. Therefore, we now want to find $` X_k `$ with the property: 
```math
x_n = \frac1N\sum_{k=0}^{N-1} X_k y_{(kn\bmod{N})} \quad  n=0, \ldots, N-1
```

This can be written as a system of linear equations:
```math
\frac{1}{N}
\begin{bmatrix}
y_0 & y_0 & \cdots & y_0 & y_0 \\
y_0 & y_1 & \cdots & y_{N-2} & y_{N-1} \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
y_0 & y_k & \cdots & y_{(k(N-2)\bmod N)} & y_{(k(N-1)\bmod N)} \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
y_0 & y_{N-1} & \cdots & y_2 & y_1
\end{bmatrix}
\begin{bmatrix}
X_0\\
\vdots \\
\vdots \\
\vdots \\
X_{N-1}
\end{bmatrix}
=
\begin{bmatrix}
x_0\\
\vdots \\
\vdots \\
\vdots \\
x_{n-1}
\end{bmatrix}
```

The system, written as $` \boldsymbol{x} = \frac1N A\boldsymbol{c} `$ can then be solved by inverting the matrix: 
$` \boldsymbol{c}=NA^{-1}\boldsymbol{x} `$
, assuming $` A `$ is actually invertible, which is not true for arbitrary functions $` y `$.

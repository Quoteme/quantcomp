---
title: Quantum Computing
subtitle: Problem sheet 1
author: Luca Leon Happel
date: 2022-04-09
categories: [Quantum Computing, Problem sheets]
lastmod: 2022-04-09
lang: de_DE
header-includes: 
  - \usepackage{amsthm}
  - \usepackage{braket}
  - \usepackage{bbm}
comments: true
---

# Exercise 1.1 (Complex vector spaces)

<!--
```python
i = complex(0,1)
z1 = 3 - i + (2 - i)*(-1 + i)
print(z1)
```

```python
print((2**2+2**2)**(1/2))
```
-->

## a)
 First we simplify:
$$
\begin{aligned} 
z_1 &= 3 - i + (2-i)(-1 + i) \\
    &= 3 - i + (-2 + 2i) + (i + 1) \\
    &= 3 - i + (-1 + 3i) \\
    &= 3 + (-1 + 2i) \\
    &= 2 + 2i \\
\end{aligned}
$$
This gives us the real and imaginary part $\Re(z_1)=\Im(z_1)=2$, as
well as the complex conjugate $z_1^* = 2 - 2i$ and by pythagoras theorem
the absolute value $\sqrt{2^2+2^2} = \sqrt{8}$.

## b)
![](./handschrift/abgabe01_01b.pdf)

## c)

Given that $\{ \Ket{ 0 }, \Ket{ 1 }, ..., \Ket{ d-1 }  \}$ is an
ONB, we also know that $\{ \Bra{ 0 }, \Bra{ 1 }, ..., \Bra{ d-1 }  \}$
is an ONB of the dual-space ${\mathbb{C}^d}^*$ with
$\Braket{ i | j } = \delta_{ij}$.

Therefore given a ket $\Ket{ \psi }$ which has a decomposition into
basis vectors $\sum_{k=0}^{d-1} \psi_k \Ket{ k }$, because ${\mathbb{C}^d}^*$
is a vector space, we can find the $\psi_i$ by
$$\begin{aligned}
\Braket{ i | \psi } &= \Bra{ i }\sum_{k=0}^{d-1} \phi_k \Ket{ k } \\
                    &= \delta_{0i}\psi_0 + \dots + \delta_{ii}\phi_i + \dots + \delta_{i(d-1)}\phi_{d_1} \\
                    &= \psi_i
\end{aligned}$$

## d)

A Hilbert space H is a real or complex inner product space that is
also a complete metric space with respect to the distance function
induced by the inner product.

We already know that $\mathbb{C}^d$ is a complete vector space under the
euclidean norm. Moreover it is also a complete vector space under the
induced distance function of the inner product, defined by:
$$\langle x,y \rangle = y^\dagger x = \bar{y^t}x$$
<!--
$$
\left(
    \begin{array}{c}
    a_1 \\
    \vdots \\
    a_d \\
    \end{array}
\right)
\cdot
\left(
    \begin{array}{c}
    b_1 \\
    \vdots \\
    b_d \\
    \end{array}
\right)
= \bar b_1 a_1 + \dots + \bar b_d a_d
$$
-->
we therefore only need to check that $\langle \cdot, \cdot \rangle$
is an inner product.

1. We have _conjugate symmetry_:
    $$\begin{aligned}
     \overline{\langle y,x \rangle} &= \overline{\bar{x^t}y} \\
      &= x^t\bar y \\
      &= \bar{y^t} x \\
      &= y^\dagger x \\
      &= \langle x,y \rangle \\
    \end{aligned}
    $$
2. We have _linearity in the first argument_:
    $$\begin{aligned}
    \langle \lambda x_1 + \mu x_2, y \rangle &= \bar{y^t}(\lambda x_1 + \mu x_2) \\
    &= \left(\begin{array}{ccc}\bar y_1 & \dots & \bar y_d\end{array}\right)
    \left(
        \begin{array}{c}
        \lambda x_{1_1} + \mu x_{2_1} \\
        \vdots \\
        \lambda x_{1_d} + \mu x_{2_d}\\
        \end{array}
    \right) \\
    &= \left(\begin{array}{ccc}\bar y_1 & \dots & \bar y_d\end{array}\right)
    \left(
        \left(
            \begin{array}{c}
            \lambda x_{1_1} \\
            \vdots \\
            \lambda x_{1_d} \\
            \end{array}
        \right)
        +
        \left(
            \begin{array}{c}
            \mu x_{2_1} \\
            \vdots \\
            \mu x_{2_d} \\
            \end{array}
        \right)
    \right) \\
    &= \left(\begin{array}{ccc}\bar y_1 & \dots & \bar y_d\end{array}\right)
        \left(
            \begin{array}{c}
            \lambda x_{1_1} \\
            \vdots \\
            \lambda x_{1_d} \\
            \end{array}
        \right)
        +
        \left(\begin{array}{ccc}\bar y_1 & \dots & \bar y_d\end{array}\right)
        \left(
            \begin{array}{c}
            \mu x_{2_1} \\
            \vdots \\
            \mu x_{2_d} \\
            \end{array}
        \right) \\
    &= \lambda
        \left(\begin{array}{ccc}\bar y_1 & \dots & \bar y_d\end{array}\right)
        \left(
            \begin{array}{c}
            x_{1_1} \\
            \vdots \\
            x_{1_d} \\
            \end{array}
        \right)
        +
        \mu
        \left(\begin{array}{ccc}\bar y_1 & \dots & \bar y_d\end{array}\right)
        \left(
            \begin{array}{c}
            x_{2_1} \\
            \vdots \\
            x_{2_d} \\
            \end{array}
        \right) \\
    &= \lambda \langle x_1,y \rangle + \mu \langle x_2, y \rangle
    \end{aligned}
    $$
3. We have that the inner product of an element with itself is _positive-definite_:
    $$\begin{aligned}
    \langle x,x \rangle &= \bar{x^t} x \\
    &=
    \left(\begin{array}{ccc}\bar x_1 & \dots & \bar x_d\end{array}\right)
    \left(
        \begin{array}{c}
        x_1 \\
        \vdots \\
        x_d \\
        \end{array}
    \right) \\
    &=
    \underbrace{
    \underbrace{\bar x_1 x_1}_{\substack{=0 \Leftrightarrow x_1 = 0 \\ >0 \, \forall x_1}}
    + \dots +
    \underbrace{\bar x_d x_d}_{\substack{=0 \Leftrightarrow x_d = 0 \\ >0 \, \forall x_d}}
    }_{\substack{=0 \Leftrightarrow x=0 \\ >0 \, \forall x}}
    \end{aligned}
    $$

# Exercise 1.2 (Postulates: Quantum states and their transformations)

## a)

$$\begin{aligned}
Y &= \left(\begin{array}{cc}
1 & -i \\
i & 1 \\
\end{array}\right) \\
Y^\dagger &= \left(\begin{array}{cc}
\bar 1 & \bar{-i} \\
\bar i & \bar 1 \\
\end{array}\right)^t
 = \left(\begin{array}{cc}
 1 & i \\
 -i &  1 \\
\end{array}\right)^t
 = \left(\begin{array}{cc}
 1 & -i \\
 i &  1 \\
\end{array}\right)
= Y
\end{aligned} \\
$$


## b)

$M \in U(\mathbb{C}^{3\times 3}) \Leftrightarrow M^\dagger M = \mathbbm{1}_{\mathbb{C}^3}$

$$
\begin{aligned}
\det(M) &= \cos(\theta)^2e^{i\phi}-i\sin(\theta)i\sin(\theta)e^{i\phi} \\
 &= e^{i\phi}(\cos(\theta)^2+\sin(\theta)\sin(\theta)) \\
 &= e^{i\phi}(\cos(\theta)^2+\sin(\theta)^2) \\
 &= e^{i\phi} \\
\end{aligned}
$$

Therefore $|det(M)|\neq 1$ for all $\phi, \theta \in \mathbb{R}$

$$
\left(
\begin{array}{ccc}
\cos(\theta) & 0 & -i\sin(\theta) \\
0 & e^{i\phi} & 0 \\
-i\sin(\theta) & 0 & \cos(\theta) \\
\end{array}
\right)^\dagger =
\left(
\begin{array}{ccc}
\cos(\theta) & 0 & i\sin(\theta) \\
0 & e^{-i\phi} & 0 \\
i\sin(\theta) & 0 & \cos(\theta) \\
\end{array}
\right)
$$

$$
\begin{aligned}
\left(
\begin{array}{ccc}
\cos(\theta) & 0 & -i\sin(\theta) \\
0 & e^{i\phi} & 0 \\
-i\sin(\theta) & 0 & \cos(\theta) \\
\end{array}
\right)
\left(
\begin{array}{ccc}
\cos(\theta) & 0 & i\sin(\theta) \\
0 & e^{-i\phi} & 0 \\
i\sin(\theta) & 0 & \cos(\theta) \\
\end{array}
\right) \\ = 
\left(
    \begin{array}{ccc}
    \cos(\theta)^2+\sin(\theta)^2 & 0 & i\cos(\theta)\sin(\theta)-i\sin(\theta)\cos(\theta) \\
    0 & e^{i\phi}e^{-i\phi} & 0 \\
    -i\sin(\theta)\cos(\theta)+\cos(\theta)i\sin(\theta) & 0 & -i^2\sin(\theta)^2+\cos(\theta)^2 \\
    \end{array}
\right) \\ =
\left(
    \begin{array}{ccc}
    1 & 0 & 0 \\
    0 & e^{i\phi-i\phi} & 0 \\
    0 & 0 & 1 \\
    \end{array}
\right) \\ =
\left(
    \begin{array}{ccc}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    0 & 0 & 1 \\
    \end{array}
\right)
\end{aligned} \\
$$

Finally we can conclude that for all $\phi, \theta \in \mathbb{C}$
the matrix $M$ is unitary.

## c)

$$H \Ket{ 0 } = \frac{1}{\sqrt{2}}\begin{pmatrix}
1 & 1 \\
1 & -1 \\
\end{pmatrix}\begin{pmatrix}
1 \\
0 \\
\end{pmatrix} = \frac{1}{\sqrt 2}\begin{pmatrix}1 \\ 1\end{pmatrix}$$

$$H \Ket{ 1 } = \frac{1}{\sqrt{2}}\begin{pmatrix}
1 & 1 \\
1 & -1 \\
\end{pmatrix}\begin{pmatrix}
0 \\
1 \\
\end{pmatrix} = \frac{1}{\sqrt 2}\begin{pmatrix}1 \\ -1\end{pmatrix}$$

There cannot be another matrix that describes the same linear transformation.
I am unsure what is meant with:
> any other unitary matrices that describe the same transformation of states?
Does this mean the same linear transformation?

# 1.3 (Observables)

## a)

We need $M^\dagger = M$ or equivalently $a_{ij} = \bar a_{ji}$ for a matrix 
to be hermitian. For the special case 
$$\begin{bmatrix}a & b \\ c & d\end{bmatrix}$$
we have $a=\bar a$, $b = \bar c$ and $d = \bar d$

## b)

<!-- Based on [https://physics.stackexchange.com/questions/342738/meaning-of-a-bra-ket-inner-product](https://physics.stackexchange.com/questions/342738/meaning-of-a-bra-ket-inner-product) -->
Assume $M$ is self-adjoint and given a choice of orthonormal basis vectors
$(e_i)_{1\le i \le d}$ we choose the following representation 
$$
\Ket{ \phi } =
\begin{bmatrix}
\psi_1 \\
\vdots \\
\psi_d \\
\end{bmatrix}
\quad
\Bra{ \phi } =
\begin{bmatrix}
\bar \psi_1
\dots 
\bar \psi_d 
\end{bmatrix}
\quad
M = \begin{bmatrix}
m_{11} & m_{12} & \dots & m_{1d} \\
\overline{ m_{12}} & \ddots & &  \vdots \\
\vdots & & \ddots & \vdots \\
\overline{ m_{1d}} & \dots & \dots& m_{dd} \\
\end{bmatrix}
$$
We can now calculate the following using the fact that $M$ is a linear operator[^notation_linear_operator] :
$$
\begin{aligned}
 \Braket{ \psi | M | \psi } &= \Bra{ \psi } (M \Ket{ \psi }) = (\Bra{ \psi } M) \Ket{ \psi } \\
 &= \psi^\dagger (M \psi) \\
 &= 
%
\begin{bmatrix}
\bar \psi_1
\dots 
\bar \psi_d 
\end{bmatrix}
%
\begin{bmatrix}
m_{11} & m_{12} & \dots & m_{1d} \\
\overline{ m_{12}} & \ddots & &  \vdots \\
\vdots & & \ddots & \vdots \\
\overline{m_{1d}} & \dots & \dots& m_{dd} \\
\end{bmatrix}
%
\begin{bmatrix}
\psi_1 \\
\vdots \\
\psi_d \\
\end{bmatrix} \\
%
&=
%
\begin{bmatrix}
\bar \psi_1
\dots 
\bar \psi_d 
\end{bmatrix}
%
\begin{bmatrix}
m_{11}\psi_1 + \dots + m_{1d} \psi_d \\
\vdots \\
\overline{m_{1d}}\psi_1 + \dots + m_{dd} \psi_d \\
\end{bmatrix} \\
%
&=
%
\sum_{k=1}^d \bar \psi_k \left(\sum_{l=1}^d m_{kl}\psi_l\right) \\
&=
\underbrace{\sum_{k=1}^d m_{kk} \bar \psi_k \psi_k}_{\in \mathbb{R}}
+
\underbrace{\sum_{k=2}^d \sum_{l=1}^{k-1} m_{kl}\bar \psi_k \psi_l + \overline{m_{kl}} \bar \psi_l \psi_k }_{\in \mathbb{R}}
\end{aligned}
$$

The right underbrace can be checked by writing
$m_{kl} = (a+bi), \psi_k = (c+di), \dots$ and then multiplying out.

## c)


$$
\begin{aligned}
\Braket{ 1 | \sigma_x | 1 }
&=
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
0
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 1 | \sigma_y | 1 }
&=
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} -i \\ 0 \end{bmatrix}
\\
&= 
0
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 1 | \sigma_z | 1 }
&=
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 0 \\ -1 \end{bmatrix}
\\
&= 
-1
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 0 | \sigma_x | 0 }
&=
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
0
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 0 | \sigma_y | 0 }
&=
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 0 \\ i \end{bmatrix}
\\
&= 
0
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 0 | \sigma_z | 0 }
&=
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
1
\end{aligned}
$$

## d)

Due to the associativity of matrix-multiplication, we can calculate
$\Braket{ v | (X Y) | v }$ instead of $\Bra{ v } X (Y\Ket{ v })$.
Therefore applying the Pauli observables to $H \ket{ 0 }$ and $H \Ket{ 1 }$ yields:

$$
\begin{aligned}
\Braket{ 1 | (\sigma_x H) | 1 }
&=
\begin{bmatrix} 0 & 1 \end{bmatrix}
\left(
    \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
    \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\right)
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 1 & -1 \\ 1 & 1 \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} -1 \\ 1 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 1 | (\sigma_y H) | 1 }
&=
\begin{bmatrix} 0 & 1 \end{bmatrix}
\left(
    \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}
    \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\right)
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} -i & i \\ i & i \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\frac{i}{\sqrt 2}
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 1 | (\sigma_z H) | 1 }
&=
\begin{bmatrix} 0 & 1 \end{bmatrix}
\left(
    \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
    \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\right)
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 0 & 1 \end{bmatrix}
\begin{bmatrix} 1 & 1 \\ -1 & 1 \end{bmatrix}
\begin{bmatrix} 0 \\ 1 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 0 | (\sigma_x H) | 0 }
&=
\begin{bmatrix} 1 & 0 \end{bmatrix}
\left(
    \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
    \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\right)
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 1 & -1 \\ 1 & 1 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 0 | (\sigma_y H) | 0 }
&=
\begin{bmatrix} 1 & 0 \end{bmatrix}
\left(
    \begin{bmatrix} 0 & -i \\ i & 0 \end{bmatrix}
    \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\right)
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} -i & i \\ i & i \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\frac{-i}{\sqrt 2}
\end{aligned}
$$

$$
\begin{aligned}
\Braket{ 0 | (\sigma_z H) | 0 }
&=
\begin{bmatrix} 1 & 0 \end{bmatrix}
\left(
    \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
    \frac{1}{\sqrt 2} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\right)
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\begin{bmatrix} 1 & 0 \end{bmatrix}
\begin{bmatrix} 1 & 1 \\ -1 & 1 \end{bmatrix}
\begin{bmatrix} 1 \\ 0 \end{bmatrix}
\\
&= 
\frac{1}{\sqrt 2}
\end{aligned}
$$

[^notation_linear_operator]: [https://en.wikipedia.org/wiki/Bra%E2%80%93ket_notation#Linear_operators](https://en.wikipedia.org/wiki/Bra%E2%80%93ket_notation#Linear_operators)

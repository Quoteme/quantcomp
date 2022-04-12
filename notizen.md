---
title: First Post
lang: de_DE
header-includes:
  - \usepackage{amsthm}
  - \usepackage{cleveref}
  - \usepackage{braket}
---
# Vorlesung 2

\newtheorem{theorem}{Theorem}[section]
\newtheorem*{theorem*}{Theorem}
\newtheorem{proposition}[theorem]{Proposition}
\newtheorem{korollar}[theorem]{Korollar}
\newtheorem{lemma}[theorem]{Lemma}
\theoremstyle{definition}
\newtheorem{definition}[theorem]{Definition}

\begin{definition}
    $F\in L(V,W)$ can be represented by a matrix $A\in C^{n\times m}$
    with $n=\dim V$ and $m=\dim W$
    when basises are chosen.
\end{definition}

\begin{definition}[Complex Hilbert space]
    A complete (every cauchy sequence converges)
    complex vector space $\mathcal{H}$ with a sequilinear inner product
    $$ \langle \cdot, \cdot \rangle : \mathcal{H} \times \mathcal{H} \rightarrow \mathbb{C}$$
\end{definition}

\begin{definition}
    A Basis $(e_1, \dots, e_n) \subset \mathcal{H}$ with
    $$\langle e_i, e_j \rangle = \delta_{ij}$$
\end{definition}

\begin{definition}
    We define the dual space
    $$\mathcal{H}^* = \{f:\mathcal{H} \overset{linear}{\to} \mathbb{C}\}$$
\end{definition}

\begin{definition}
    \[\begin{aligned}
        \mathcal{H}^* &= \{f:\mathcal{H} \overset{linear}{\to} \mathbb{C}\} \\
        &= \{\langle x,\cdot \rangle | x \in \mathcal{H}\}
    \end{aligned}\]
\end{definition}

We will use the [bra-ket notation](https://en.wikipedia.org/wiki/Bra%E2%80%93ket_notation):

\begin{definition}[bra-ket Notation]
    $\varphi, \psi \in \mathcal{H}$:
    \[\begin{aligned}
        \varphi &= | \varphi \rangle \in \mathcal{H} & \text{bra} \\
        \langle \varphi , \cdot \rangle &= \langle \varphi | \in L(\mathcal{H}) & \text{ket} \\
        \langle \varphi , \psi \rangle &= \langle \varphi | \psi \rangle
    \end{aligned}\]
\end{definition}

![Example of BraKet](./notizen/vl2_ex1.png)

\begin{definition}[Rank-1 operators]
    Let $| \psi \rangle, | \varphi \rangle\in \mathcal{H}$
    The "\textit{Outer product}" acts on $| \eta \rangle\in \mathcal{H}$
    as
    $$ (| \psi \rangle \langle \varphi |)(| \eta \rangle) = | \psi \rangle \langle \varphi | \eta \rangle$$
\end{definition}

\begin{definition}[self-adjoint operators, aka. Hermitian operators]
    $$\text{Herm}(\mathcal{H}) = \{ A \in L(\mathcal{H}) | A^\dagger = A\}$$
\end{definition}

\begin{definition}[unitary operators]
    $$U(\mathcal{H}) = \{ A \in L(\mathcal{H}) | A^\dagger = A^{-1}\}$$
\end{definition}

\begin{definition}[normal operators]
    $$\{ A \in L(\mathcal{H}) | A^\dagger A = A A^\dagger\}$$
    is the set of normal operators
\end{definition}

\begin{proposition}
    $A\in L(\mathcal{H})$ ist \textit{diagonalizable} if there is a
    basis of eigenvectors
\end{proposition}

# Vorlesung 3

Di 12. Apr 12:41:34 CEST 2022

\begin{proposition}[diagonalizable (continued)]
    $A\in L(\mathcal{H}$ is \underline{unitarily diagonalizable} if there
    is an orthonormalbasisoof eigenvectors of A
\end{proposition}

\begin{theorem}
    Let $A\in L(\mathcal{H}$.
    $A$ is \underline{uniformly diagonalizable}
    $\Leftrightarrow$ $A$ is invertible
\end{theorem}

\begin{theorem}[spectral decomposition]
    $A\in L(\mathcal{H}$ normal, $n=\dim(\mathcal{H}$.
    then
    $$A=\sum_{j=1}^n a_j \Ket{ a_j }\Bra{ a_j }$$
    for eigenvalues $a_i,\dots,a_n$ of $A$ and corresponding
    eigenvectors $\Ket{ a_1 },\dots,\Ket{ a_n }$.
\end{theorem}

Why do we call a matrix which is normal (ie $AA^\dagger = A^\dagger A$)
_unitarily diagonalizable_? 

Consider $\mathcal{H}=\mathbb{C}^d$ and $A\in L(\mathbb{C}^n)$ normal.
We set $U=\left[\Ket{ a_1 },\dots,\Ket{ a_n }\right]$ which is a matrix
that has as its collumns the eigenvectors of $A$.
We can now calculate
$U^\dagger = \begin{bmatrix} \Bra{ a_1 } \\ \vdots \\ \Bra{ a_n } \\ \end{bmatrix}$
which leads to 
$$U^\dagger U = \begin{bmatrix}
\Braket{ a_1 | a_1 } & \Braket{ a_1 | a_2 } & \dots & \Braket{ a_1 | a_n } \\
\Braket{ a_2 | a_1 } & \Braket{ a_2 | a_2 } &  & \vdots \\
\vdots &  & \ddots & \vdots \\
\Braket{ a_n | a_1 } & \dots &  & \Braket{ a_n | a_n } \\
\end{bmatrix} = \boldsymbol 1_{\mathbb{C}^{n\times n}}$$
Therefore every normal matrix has a is uniformly diagonalizable.

\begin{definition}[positive semi-definite operators]
$A\in\text{Herm}(\mathcal{H}$ is positive semi-definite (PSD)
if 
$$\Braket{ \psi | A | \psi }\ge 0, \quad \forall \Ket{ \psi }\in \mathcal{H}$$
Notation 
$$A\ge 0$$
\end{definition}

\begin{definition}
$$\text{spec}(A) = \{ a_j\in \mathbb{C} | a_j \text{ is an eigenvector of } A \}$$
\end{definition}

Let $A$ be normal.
Then $\text{spec}(A^\dagger)=\overline{\text{spec}(A)} = \{ \overline{a_j} \}_j$

| $A$ is ... | relation to $\text{spec}(A)$ |
|---|---|
| self-adjoint | $\text{spec}(A)\subset \mathbb{R}$ |
| unitary | $\text{spec}(A) \subset \{ e^{i\phi} | \phi \in \mathbb{R} \}$
| positive semi-definite | $\text{spec}(A) \subset \mathbb{R}_0^+$
| a projector ($A^2=A$) | $\text{spec}(A) \subset \{ 0,1 \}$

\begin{theorem}
    $$A=\sum_{j=1}^n \underbrace{a_j}_{\text{degenerate in general}(\exists i\neq j: a_i=a_j)} \underbrace{\Ket{ a_j }\Bra{ a_j }}_{\text{rank} 1}$$
\end{theorem}

# Chapter 2: Quantum mechanics

## Preparation: probability theory (finite sample spaces)

goal::include amplitudes of our vectors $\Ket{ 0 }, \Ket{ 1 }, \dots$

\begin{definition}[probability vector]

A vector $p\in \mathbb{R}1d$ is a \underline{probability vector}
if 
$$p_i \ge 0, \quad \sum_{i=1}^d p_i=1$$
\end{definition}

\begin{definition}[random variables]
    $A$ with $d$ outcomes from $\left(a_1, \dots, a_d\right)\subset \mathbb{R}$.
    $A$ is a function associated with  a probability vector $p$
    $$\mathbb{P}[i] = \mathbb{P}\left[A \underset{\wedge}{=} a_i\right] = p_i$$
\end{definition}

## Quantum mechanical notation

### Replace 

$$\begin{aligned}
p &\to \rho=\text{diag}(p) \\
A &\to A=\text{diag}(a_1,\dots,a_d)
\end{aligned}$$

### Implications

- $\text{Tr}[\rho] = \sum_i p_i = 1$
- $\langle A \rangle = \text{Tr}(\rho A)$
- $A = \sum_{a\in\text{spec}(A)}aP_a$
    - $A = \begin{bmatrix}
     a_1 &  & & \\
     & a_2 & & \\
     &  & \ddots & \\
     &  &  & a_d\\
    \end{bmatrix} \overset{a_1 = a_2 = a}{=} \begin{bmatrix}
     a &  & & \\
     & a & & \\
     &  & \ddots & \\
     &  &  & a_d\\
    \end{bmatrix} \Rightarrow P_a = \begin{bmatrix}
     1 &  & & \\
     & 1 & & \\
     &  & \ddots & \\
     &  &  0\\
    \end{bmatrix}$
- $\mathbb{P}[a] = \mathbb{P}[A=a] = \sum_{j: a_j = a}p_j = \text{Tr}[P_{a\rho}]$

## interpretations of probabilities: lack of knowledge

conditioned on observing $a$:
$$\begin{aligned}
 \rho &\to \rho_a = \Ket{ a }\Bra{ a } & \text{non-degenerate case}\\
 \rho &\to \rho_a = \frac{P_a \rho P_a}{\text{Tr}[P_a \rho]} & \text{general case}\\
\end{aligned}$$

_Check:_ Say $a_1 = a_2 = \dots = a_r = a, \quad a_r+1, \dots , a_d$
conditional probability of $j\in [r]$
$$\mathbb{P}[j] = \frac{\mathbb{P}[j \text{ AND } A = a]}{\mathbb{P}[A=a]} = \frac{p_j}{\sum_{j\in[r]}p_j} = \frac{p_{jj}}{\text{Tr}(P_a\rho)}$$

\begin{definition}[ density operator ]
The set of density operators $\rho$ is :
$$S(\mathcal{H}:=\{ \rho\in\text{Herm}(\mathcal{H}) | \rho\ge 0, \, \text{Tr}[\rho]=1 \}$$
\end{definition}

\begin{proposition}

$$\rho_1,\rho_2\in S(\mathcal{H}), \, \lambda\in[0,1] \\ \lambda \rho_1 + (1-\lambda)\rho_2 \in S(\mathcal{H})$$

\end{proposition}


<!--
TODO: Add sums to snippets
lemmas, definitions and so on should have [] options
overline RR,CC,dagger, spec, left[\right], \left\{l\right\}
no mote line breaks on $$$$
-->

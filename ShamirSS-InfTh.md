# Shamir Secret Sharing - Information Theoretic Proof

## Goal
Prove that for any group of fewer than $t$ participants, their shares (generated with a Shamir Secret Sharing scheme) provide no information about the secret $s$.

Formally, for less than $t$ shares, the distribution of these shares is independet of the secret $s$.

## Shamir Secret Sharing Scheme
Given a secret $s$, a Shamir Secret Sharing (SSS) scheme allows a dealer to generate a set of shares $\{s_1, s_2, ...\}$ with a certain threshold $t$, i.e., at least $t$ shares are needed to reconstruct the secret $s$.

For that, the dealer generates a polynomial of degree $k = t-1$ with randomly sampled coefficients:

$$
P(X) = s + a_1 \cdot x + a_2 \cdot x^2 + ... + a_k \cdot x^k
$$

To generate a set of $n$ shares, we need a list of indexes $D = \{x_1, x_2, ..., x_n\}$ with $x_i \in \mathbb{N}$. Then, share $i$ is computed as the evaluation of the polynomial $P(x_i)$.

The secret can be reconstructed from the shares by using interpolation. A polynomial of degree $k$ can be interpolated from $k+1$ points. Therefore, given a set of points $\{(x_1, P(x_1)), (x_2, P(x_2)), ..., (x_{k+1}, P(x_{k+1}))\}$, one can interpolate $P(X)$ and compute the secret as $P(0) = s$.

## Definitions

### Mutual Information

The mutual information $I(X; Y)$ of two random variables $X$ and $Y$ is a measure of the mutual dependence between the two variables.

## Proof

Given $S$ the random variable for the secret space, and $X$ the random variable for the shares given $k < t$ parties, we want to prove that $I(S; X) = 0$, i.e., that $S$ and $X$ are mutually independent when we have less than $t$ shares.

If we have a set of points $\{(x_1, P(x_1)), (x_2, P(x_2)), ..., (x_k, P(x_k))\}$, the system is undetermined. In $\mathbb{R}$, there are infinitely many polynomials of degree $k$ that pass through $k$ points. In $\mathbb{F}_p$, there are $|\mathbb{F}_p|$ polynomials of degree $k$ that pass through $k$ points. In both cases, any of the possible polynomials is a valid candidate to be the generator of the secret.

Because of this, we have that $s$ is completely independent of any subset of fewer than $t$ points, and we can confirm that $I(S; X) = 0$.
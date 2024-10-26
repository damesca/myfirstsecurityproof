# OTP - Information Theoretic Proof

## Goal
Prove that the One Time Pad (OTP) has perfect secrey, i.e., the adversary learns nothing about the plaintext, even when it has unlimited computational power.

## OTP Scheme
Given a message $m$ and a key $k$, with $len(m) = len(k) = n$, the ciphertext is computed as $c = m \oplus k$.

## Definitions

### Perfect Secrecy

We want to prove that $P(m | c) = P(m)$ for all possible $m$ and $c$, i.e., that the probability distribution of the plaintext given the ciphertext is the same as the distribution of the plaintext itself.

### Uniform random key

$P(k = k') = 1/2^n$ for any $k' \in \{0,1\}^n$, i.e., all possible keys in the key space have the same probability.

## Proof

We want to prove that $P(m|c) = P(m)$. For that, we apply Bayes Theorem:

$$
P(m|c) = \frac{P(c|m)P(m)}{P(c)}
$$

First, we have that $P(c|m) = P(k) = 1/2^n$, because given a fixed $m$, $c$ is determined by a uniformly random key, i.e., $c = m \oplus k$.

Second, we have that $P(c) = 1/2^n$, because there are $2^n$ possible ciphertexts, each of which is produced by exactly one key $k$.

Finally, we substitute values in Bayes:

$$
P(m|c) = \frac{\frac{1}{2^n} P(m)}{\frac{1}{2^n}} = P(m)
$$

Therefore, since the probabilities are the same, we have concluded that the distribution of the message given a ciphertext is the same as the distribution of an independent message, i.e., the scheme has perfect secrecy.
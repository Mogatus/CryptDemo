# CryptDemo
Simple GUI demonstrating different crypt algos

## RSA
### Required Inputs and displayed fields

#### Creating keys

* Two primes p and q as input
* n = p*q as a result
* φ(n) = (p-1)*(q-1) - Eulersche Phi-function as a result (alternatively use Carmichaels lambda function λ(n))
* Choose e as input such that 1 < e < λ(n) and gcd(e, λ(n)) = 1; that is, e and λ(n) are coprime. (2^16+1 = 65537)
* Determine d as d ≡ e−1 (mod λ(n)); that is, d is the modular multiplicative inverse of e modulo φ(n) (or λ(n))

=> 
* public key: (n, e)
* private key: d


#### Encrypting

After Bob obtains Alice's public key, he can send a message M to Alice.

To do it, he first turns M (strictly speaking, the un-padded plaintext) into an integer m (strictly speaking, the padded plaintext), such that 0 ≤ m < n by using an agreed-upon reversible protocol known as a padding scheme. He then computes the ciphertext c, using Alice's public key e, corresponding to

c ≡ m^e mod (n)

This can be done reasonably quickly, even for very large numbers, using modular exponentiation. Bob then transmits c to Alice. Note that at least nine values of m will yield a ciphertext c equal to m,[a] but this is very unlikely to occur in practice.


#### Decrypting

Alice can recover m from c by using her private key exponent d by computing

c^d ≡ m^e^d ≡ m (mod) n

Given m, she can recover the original message M by reversing the padding scheme.

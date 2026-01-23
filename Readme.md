# Prime Factorization (Trial Division, Step by Step)

This repository contains a **clear, educational, and fully traceable implementation**
of **prime factorization** using **trial division up to √n**, written in Python.

The goal of this code is **clarity and correctness**, not maximum performance.
It is designed for learning, teaching, debugging, and understanding how
prime factorization works internally.

---

## Overview

Given a positive integer `n > 1`, the algorithm decomposes it into its **prime factors**
while explicitly showing:

* which candidate divisors were **tested**
* which primes were **actually found**
* how the number `n` is progressively reduced step by step

No precomputed prime lists are used.
All primes are discovered naturally through the factorization process.

---

## Algorithm Summary

1. Handle the factor **2** separately.
2. Test only **odd candidate divisors**, starting from 3.
3. Stop testing when the candidate divisor exceeds **√n**.
4. Repeatedly divide out each prime factor.
5. If a number greater than 1 remains at the end, it must be **prime**.

---

## Why stopping at √n is sufficient

If a number `n` can be written as:

```
n = a × b
```

then at least one of `a` or `b` must satisfy:

```
a ≤ √n  or  b ≤ √n
```

Otherwise:

```
a × b > √n × √n = n
```

which is impossible.

Therefore:

> If no divisor ≤ √n exists, the remaining number must be prime.

This is a fundamental result from elementary number theory and is the key
optimization used by the algorithm.

---

## Logical Flow Diagram

The complete logic of the algorithm is summarized below:

```
START
 │
 │  n given
 │
 ├── Handle factor 2 separately
 │
 ├── p = 3
 │
 ├── WHILE p² ≤ n
 │      │
 │      ├── tested_primes.append(p)
 │      │
 │      ├── IF n % p == 0
 │      │      │
 │      │      ├── WHILE n % p == 0
 │      │      │      ├── count p
 │      │      │      ├── n = n / p
 │      │      │      └── found_primes.append(p)
 │      │      │
 │      │      └── p fully removed
 │      │
 │      └── p = p + 2
 │
 ├── IF n > 1
 │      └── n is prime → record it
 │
 └── END
```

---

## Data Structures Used

### `factors`

A dictionary mapping each prime factor to its exponent:

```
{ prime : exponent }
```

Example:

```
{2: 3, 3: 2, 7: 1}
```

---

### `tested_primes`

A list containing **all candidate divisors that were tested**, regardless of
whether they divided `n` or not.

Purpose:

* shows the search path
* useful for debugging and educational tracing

---

### `found_primes`

A list containing **only the prime factors that were actually found**,
including duplicates, in the order they were extracted.

Example:

```
[2, 2, 2, 3, 3, 3, 5, 7]
```

Purpose:

* shows how `n` is decomposed step by step
* reflects the multiplicity of each prime factor

---

## Efficiency

* **Time complexity:**
  `O(√n)` in the worst case (standard trial division)

* **Space complexity:**
  `O(log n)` for storing prime factors

This algorithm is **not optimal for very large integers**, but it is:

* deterministic
* mathematically transparent
* easy to verify and debug
* ideal for educational and exploratory use

---

## Intended Use

* Learning how prime factorization works internally
* Teaching trial division and the √n optimization
* Step-by-step tracing and debugging
* Small to medium-sized integers

For cryptographic-scale integers, more advanced algorithms
(e.g. Pollard Rho, Miller–Rabin) should be used instead.

---

## License

MIT License (or adapt as needed).

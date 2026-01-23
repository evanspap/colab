# Prime Factorization (Trial Division, Step by Step)

This repository contains a **clear and educational implementation of prime factorization**
using **trial division up to √n**, written in Python.

The goal of this code is **clarity and correctness**, not ultimate performance.
It is suitable for learning, teaching, debugging, and exploratory number theory.

---

## Overview

Given a positive integer `n > 1`, the algorithm decomposes it into its **prime factors**
and records:

- which candidate divisors were **tested**
- which primes were **actually found**
- how `n` is progressively reduced step by step

The implementation avoids precomputed prime lists and works directly from first principles.

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



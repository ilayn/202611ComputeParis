---
theme: default
title: Optimized BLAS
info: Cache hierarchy, blocking, and why SciPy dropped Fortran
transition: slide-left
mdc: true
---

# Optimized BLAS

Cache hierarchy, blocking, and the end of Fortran in SciPy

<!--
Speaker notes go in an HTML comment at the end of a slide.
They show up in presenter mode (press `p`, or open /presenter).
-->

---

# Why blocking matters

Ideal-reuse arithmetic intensity, fp64:

$$
I = \frac{2mnk}{8\,(mk + kn + 2mn)} \quad \text{flop/byte}
$$

<v-click>

For $m = n = k$: $I = n/16$, so it grows linearly in $n$, *if* the working set fits in cache.

</v-click>

---

# From naive to blocked

````md magic-move
```c
for (i = 0; i < n; i++)
  for (j = 0; j < n; j++)
    for (k = 0; k < n; k++)
      C[i][j] += A[i][k] * B[k][j];
```
```c
for (i = 0; i < n; i++)
  for (k = 0; k < n; k++)
    for (j = 0; j < n; j++)
      C[i][j] += A[i][k] * B[k][j];
```
```c
for (ii = 0; ii < n; ii += NB)
  for (kk = 0; kk < n; kk += NB)
    for (jj = 0; jj < n; jj += NB)
      kernel(&C[ii][jj], &A[ii][kk], &B[kk][jj], NB);
```
````

---
layout: two-cols
---

# Figures

Put SVGs in `public/figures/` and reference them from the root:

```md
<img src="/figures/roofline.svg" />
```

::right::

Vue components in `components/` are auto-imported, so `<TileGrid />` works on any slide without an import.

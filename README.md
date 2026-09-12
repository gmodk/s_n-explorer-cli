# \(S_n\) Explorer — Command-Line Application

A Python command-line application for exploring the **symmetric group**
\[
S_n,
\]
the group of all permutations of \(\{1,\dots,n\}\).

The project is intended as an interactive laboratory for finite-group theory. It lets you construct and inspect permutations, compute group operations, explore Cayley tables, generate dihedral groups as permutation groups, enumerate subgroups, identify normal subgroups, and construct quotient groups.

---

## Features

The command-line explorer supports the following operations:

1. **Compose two permutations**
   - Compute \(\sigma\circ\tau\).
   - Display the resulting permutation.

2. **Inspect a permutation**
   - One-line notation.
   - Disjoint-cycle decomposition.
   - Order.
   - Sign / parity.
   - Inverse.

3. **List all elements of \(S_n\)**
   - Generate all \(n!\) permutations of \(\{1,\dots,n\}\).

4. **List inverses**
   - Compute the inverse of every permutation in the group.

5. **Find self-inverse elements**
   - Identify all permutations satisfying
     \[
     \sigma^{-1}=\sigma.
     \]

6. **Generate the Cayley table**
   - Construct the multiplication table of \(S_n\) under permutation composition.

7. **Construct a dihedral group**
   - Build \(D_m\) as a subgroup of \(S_m\).
   - Display rotations and reflections as permutations.
   - Show an ASCII representation of the regular \(m\)-gon.

8. **Enumerate subgroups**
   - Generate the subgroups of the selected finite group.
   - Identify which subgroups are normal.

9. **Construct quotient groups**
   - For a normal subgroup \(H\trianglelefteq G\), compute the cosets of
     \[
     G/H.
     \]

---

## Mathematical model

### The symmetric group

The symmetric group on \(n\) symbols is

\[
S_n=\{\sigma:\{1,\dots,n\}\to\{1,\dots,n\}\mid \sigma
\text{ is bijective}\}.
\]

Its order is

\[
|S_n|=n!.
\]

The group operation is **composition of permutations**.

### Composition convention

The explorer uses

\[
(\sigma\circ\tau)(i)=\sigma(\tau(i)).
\]

Therefore, in

\[
\sigma\circ\tau,
\]

the permutation \(\tau\) acts first and \(\sigma\) acts second.

### Cycle decomposition

Every permutation can be written as a product of disjoint cycles. For example,

\[
\sigma=
\begin{pmatrix}
1&2&3&4\\
2&1&4&3
\end{pmatrix}
\]

has cycle decomposition

\[
(1\ 2)(3\ 4).
\]

### Order of a permutation

If the disjoint cycles of \(\sigma\) have lengths

\[
\ell_1,\ell_2,\dots,\ell_k,
\]

then

\[
\operatorname{ord}(\sigma)
=
\operatorname{lcm}(\ell_1,\ell_2,\dots,\ell_k).
\]

### Sign

The sign homomorphism is

\[
\operatorname{sgn}:S_n\to\{-1,+1\}.
\]

An even permutation has sign \(+1\), while an odd permutation has sign \(-1\).

### Normal subgroups

A subgroup \(H\le G\) is normal when

\[
gHg^{-1}=H
\qquad
\text{for every }g\in G.
\]

Only normal subgroups can be used to construct quotient groups.

### Quotient groups

If

\[
H\trianglelefteq G,
\]

then the quotient group is

\[
G/H=\{gH:g\in G\},
\]

whose elements are cosets of \(H\).

---

## Project structure

```text
s_n explorer/
├── main.py
└── symmetric_group.py
```

### `main.py`

Implements the interactive command-line interface:

- reads the value of \(n\);
- displays the operation menu;
- receives permutation selections;
- prints results returned by the mathematical engine.

### `symmetric_group.py`

Contains the group-theoretic implementation:

- generation of permutations;
- composition;
- inverses;
- cycle decomposition;
- permutation order;
- sign / parity;
- Cayley tables;
- dihedral groups;
- subgroup generation;
- subgroup enumeration;
- normality testing;
- cosets;
- quotient groups.

The mathematical logic is therefore separated from the terminal interaction.

---

## Requirements

- Python 3
- No special mathematical software is required.

Check your installation with:

```bash
python --version
```

On Windows, depending on your configuration, you can also use:

```bash
py --version
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/danielsfrede/python_projects.git
```

Move into the command-line project directory:

```bash
cd python_projects/"s_n explorer"
```

No build step is required.

---

## Running the explorer

Run:

```bash
python main.py
```

or on Windows:

```bash
py main.py
```

Choose the value of \(n\) when prompted, then select an operation from the interactive menu.

For example, choosing

\[
n=3
\]

constructs

\[
S_3,
\]

which contains

\[
|S_3|=3!=6
\]

permutations.

---

## Example: \(S_3\)

The elements of \(S_3\) are

\[
e,\quad
(1\ 2),\quad
(1\ 3),\quad
(2\ 3),\quad
(1\ 2\ 3),\quad
(1\ 3\ 2).
\]

Its basic structure includes:

- order:
  \[
  |S_3|=6;
  \]

- three transpositions of order \(2\);

- two \(3\)-cycles of order \(3\);

- alternating subgroup:
  \[
  A_3=\{e,(1\ 2\ 3),(1\ 3\ 2)\};
  \]

- normal subgroup:
  \[
  A_3\trianglelefteq S_3;
  \]

- quotient:
  \[
  S_3/A_3\cong C_2.
  \]

This makes \(S_3\) a useful first group for exploring most of the application's functionality.

---

## Dihedral groups

The explorer can construct the dihedral group \(D_m\), the symmetry group of a regular \(m\)-gon.

It is generated by a rotation \(r\) and a reflection \(s\) satisfying

\[
r^m=e,
\qquad
s^2=e,
\qquad
srs=r^{-1}.
\]

The group contains

\[
|D_m|=2m
\]

elements:

\[
D_m=
\{e,r,r^2,\dots,r^{m-1},
s,sr,sr^2,\dots,sr^{m-1}\}.
\]

In the application, these symmetries are represented concretely as permutations of the polygon's vertices.

---

## Computational limits

The size of \(S_n\) grows factorially:

| \(n\) | \(|S_n|=n!\) |
|---:|---:|
| 1 | 1 |
| 2 | 2 |
| 3 | 6 |
| 4 | 24 |
| 5 | 120 |
| 6 | 720 |
| 7 | 5,040 |
| 8 | 40,320 |

Some operations grow much faster than merely listing the elements.

A Cayley table contains

\[
(n!)^2
\]

entries.

Exhaustive subgroup enumeration is substantially more expensive because it must explore subgroup-generating combinations and repeatedly compute closure.

For that reason, the explorer is best used for structural investigation of **small symmetric groups**, particularly

\[
S_2,\ S_3,\ S_4,
\]

and selected operations on somewhat larger groups.

---

## Internal representation

Permutations are stored internally using zero-based Python indices, while mathematical output is displayed using the conventional symbols

\[
1,2,\dots,n.
\]

This allows the implementation to use natural Python list indexing without changing the standard mathematical notation shown to the user.

---

## Educational goals

The project can be used to explore several foundational ideas in abstract algebra:

- permutation groups;
- finite groups;
- cycle decompositions;
- element orders;
- parity and the alternating group;
- Cayley tables;
- generators and subgroup closure;
- normal subgroups;
- cosets;
- quotient groups;
- dihedral groups;
- concrete computational representations of abstract algebraic structures.

The central idea is to make the abstract structure of finite groups directly inspectable through computation.

---

## Repository

Source repository:

```text
https://github.com/danielsfrede/python_projects
```

Command-line project directory:

```text
s_n explorer/
```

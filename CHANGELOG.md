# Changelog — Sₙ Explorer CLI

All notable changes to the command-line version of **Sₙ Explorer** are documented in this file.

This changelog begins from the current documented project baseline. It does not attempt to reconstruct older repository history that was not explicitly reviewed.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [Unreleased]

### Documentation

- Added a dedicated `README.md` for the command-line application.
- Documented installation and execution instructions.
- Documented the composition convention
  \[
  (\sigma\circ\tau)(i)=\sigma(\tau(i)).
  \]
- Documented the internal zero-based representation and user-facing mathematical notation.
- Added computational notes concerning factorial growth, Cayley tables, and subgroup enumeration.
- Added a project-specific `.gitignore` suitable for Python development.

---

## [1.0.0] — Current documented baseline

### Added

- Interactive command-line exploration of the symmetric group \(S_n\).
- Generation of all \(n!\) permutations of \(\{1,\dots,n\}\).
- Permutation composition.
- Permutation inversion.
- Disjoint-cycle decomposition.
- Element-order computation.
- Sign and parity computation.
- Detection of self-inverse elements.
- Cayley-table generation.
- Dihedral-group construction as permutation groups.
- ASCII representation of regular polygons for dihedral exploration.
- Subgroup generation.
- Exhaustive subgroup enumeration for small groups.
- Normal-subgroup detection.
- Coset computation.
- Quotient-group construction.

### Architecture

- Separated the command-line interaction layer from the mathematical engine.
- `main.py` handles terminal interaction and menu flow.
- `symmetric_group.py` contains the group-theoretic algorithms and data structures.

### Mathematical conventions

- Composition follows right-to-left functional composition:
  \[
  (\sigma\circ\tau)(i)=\sigma(\tau(i)).
  \]
- Permutations are represented internally using zero-based Python indices.
- User-facing output uses the standard labels \(1,2,\dots,n\).

### Known limitations

- The number of elements of \(S_n\) grows factorially as \(n!\).
- Complete Cayley tables require \((n!)^2\) products.
- Exhaustive subgroup enumeration becomes computationally expensive very quickly.
- The application is therefore most practical for small symmetric groups, especially \(S_2\), \(S_3\), and \(S_4\).

---

## Notes

Future entries should be added under **Unreleased** and moved into a numbered release when a version is published.

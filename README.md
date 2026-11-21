# A ternary constant-dimension code with 6,999 codewords

The [certificate](A_3_7_4_3_6999.txt) contains 6,999 distinct 3-dimensional subspaces of GF(3)⁷ with minimum subspace distance 4. It establishes the lower bound **A₃(7, 4; 3) ≥ 6,999**.

## How the code was found

The September 5, 2026 search started with a lifted Gabidulin code over GF(81). An expurgation and augmentation step retained four graph modules indexed by the projective GF(9) representatives `1, 73, 74, 36`. The resulting core contained 6,789 planes, comprising 4,509 graph planes and 2,280 isolated point-type planes.

The C++ search started with a set of line-type planes as a warm start. On each iteration it chose a few of the 13 projection groups to rebuild and held the choices in the other groups fixed. Bounded branch-and-bound scored each compatible set by counting its line-type planes and the point-type cliques that still had at least one compatible plane. This let the search trade line-type choices against the point-type planes they made available.

With seed `61` and a cap of 30,000 branch-and-bound nodes per local search, the run reached 6,999 at iteration `23` (zero-based). The winning supplement added 130 line-type planes and one plane from each of the 80 point-type cliques, bringing the total to `6,789 + 130 + 80 = 6,999`.

## Certificate format and verification

Each line contains three decimal integers encoding the rows of a reduced row-echelon basis. Coordinate `j` of row integer `m` is `(m // 3**j) % 3` for `j = 0, …, 6`, with the least significant ternary digit first. The file has no header. Its SHA-256 with LF line endings is `971eb08bb10b86b289d02d2dfc48bb3931c64b1bfdc41531bffdd4c9510f45f0`.

Enumerating the 13 two-dimensional subspaces in each plane gives 90,987 distinct lines. No two planes share a line, so their intersections have dimension at most one and the subspace distance is at least 4. The minimum is exactly 4 because distance 6 throughout would require pairwise disjoint point sets, and GF(3)⁷ has only 1,093 one-dimensional subspaces for 6,999 planes of 13 points each.

## References

- [University of Bayreuth Subspace Codes Database](http://subspacecodes.uni-bayreuth.de/) — online tables of bounds for constant-dimension and other subspace codes.
- Daniel Heinlein, Michael Kiermaier, Sascha Kurz, and Alfred Wassermann (2019). [*Tables of subspace codes*](https://epub.uni-bayreuth.de/id/eprint/4571/) — the technical report accompanying the database.
- Ernst M. Gabidulin (1985). [*Theory of Codes with Maximum Rank Distance*](https://www.mathnet.ru/eng/ppi967) — the rank-metric code used as the starting point.
- Danilo Silva, Frank R. Kschischang, and Ralf Kötter (2008). [*A Rank-Metric Approach to Error Control in Random Network Coding*](https://arxiv.org/abs/0711.0708) — the lifting construction that turns a rank-metric code into a constant-dimension code.

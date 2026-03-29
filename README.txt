Assignment 3 - Motif Discovery

Author: Student Submission
Workspace files:
- dna.txt (input DNA sequences, one per line)
- test.ipynb (full implementation and results)

Problem setup:
- Goal: Find motif of length k = 6 from given DNA sequences.
- Implemented algorithms:
  1) Greedy Motif Search (profile-matrix-based score)
  2) Median String Algorithm (Hamming-distance-based score)

What is implemented in test.ipynb:
1. Data loading from dna.txt
2. Shared helper methods:
   - Hamming distance
   - Profile construction with pseudocounts
   - Profile-based motif score
   - Most probable k-mer selection
   - Full 4^k candidate generation
3. Greedy Motif Search:
   - Tries each k-mer seed from first sequence
   - Builds motifs across sequences using profile-most-probable k-mers
   - Tracks best motif set and score
   - Tracks score history vs step (for convergence discussion)
   - Tracks operation count using a custom counter
4. Median String Search:
   - Enumerates all 4^k candidate motifs
   - Computes total minimum Hamming distance across all sequences
   - Tracks best candidate and score
   - Tracks score history for every candidate step
   - Tracks operation count using a custom counter
5. Runtime measurement:
   - time.perf_counter() used for both algorithms
6. Plots:
   - Greedy score vs step
   - Median candidate score vs step

Output summary from current run:
- Greedy:
  - Consensus motif: gggcaa
  - Best profile-based score: 21
  - Empirical operations: 213535
  - Runtime: ~0.03 sec
- Median String:
  - Best median string: gggcaa
  - Best Hamming-distance score: 21
  - Empirical operations: 26095616
  - Runtime: ~2.27 sec

Complexity discussion:
- Greedy (dominant term): O((N-k+1)^2 * T * k)
- Median String: O(4^k * T * (N-k+1) * k)

Software requirements:
- Python 3.x
- Jupyter Notebook / VS Code Notebook support
- matplotlib (optional, used for plotting score curves)

How to run:
1. Open test.ipynb in VS Code or Jupyter.
2. Ensure dna.txt is in the same folder.
3. Run all cells from top to bottom.
4. Observe:
   - Best motifs and consensus/median outputs
   - Operation counts and runtimes
   - Score-history plots and convergence behavior notes

Notes on constraints:
- Core motif discovery logic is implemented manually.
- No motif-discovery built-in library functions are used.

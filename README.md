# Erlang Strassen Matrix Multiplication
A purely functional implementation of Strassen's Matrix Multiplication algorithm in Erlang. Built as a single-core baseline to benchmark algorithmic skeletons and multi-core parallel patterns.

This project was built as the foundational baseline for an Honours degree project focusing on parallel computing and multi-core hardware optimisation. By implementing a highly recursive Divide-and-Conquer algorithm in a functional language, this codebase is prepped to be integrated into the [Skel](https://github.com/Paraphrase/skel) algorithmic skeleton library for multi-core distributed processing.

## Features
* **Pure Funcitonal Logic:** Built entirely without `for` loops or multable state, utilising Erlang's pattern matching and list comprehenstion.
* **Dynamic Padding:** Automatically detects matrix dimensions and pads them to the nearest power of 2 (required for Strassen's recursive splitting), then trims the result.
* **Divide and Counqure Architecture:** Sub-divides matricies into quadrents and recursively calculates 7 intermediate matricies ($M_1$ - $M_2$), reducing time complexity form $O(n^3)$ to $\approx O(n^{2.81})$.
* **Parallel Ready:** The 7 intermediate matrix calculations are completely independent, serving as the perfedt stress-test for multi-threading and actor-model concurrency.

## Prerequisites 
You will need the Erlang/OTP runtime enviourment installed to compile and run this code.
* [Download Erlang](https://www.erlang.org/downloads)

## Compilation and Execution

**1.Compile the Module**
Navigate to the directory containing the source code and use the Erlang compiler (`erlc`):

```bash
erlc matrix.erl
```

**2. Run in the Erlang Shell**

```bash
$ erl
1> A = [[1, 2], [3, 4]].
2> B = [[5, 6], [7, 8]].
3> matrix:multiply(A, B).
```
(_Note: Erlang interprets lists of integers in the printable ASCII range as strings. Use `io:format("~w~n", [Result])` to print raw integers_)

## Future Scope: Parallelisation
This single core version servers as the baseline benchmark. The next phase of this project involves integrating Erlang's Actor Model (Later the Skel Libary as well) to parrallelise the recursive branches.

By wrapping the $M_1$ through $M_7$ calculation in a `Divide and Conqure` parallel pattern, the workload will be automatically distrubuted acrosse available CPU cores, demonstrating measurable performance speed up for large $N * N$ matrices.


## Resources Used
* [Learn You Some Erlang for Great Good!](https://learnyousomeerlang.com/)
* [Matrix Multiplication - Geeks for Geeks](https://www.geeksforgeeks.org/dsa/strassens-matrix-multiplication/)
* [Matrix Multiplication | Recursive: A Deep Dive into Divide-and-Conquer Algorithms](https://www.codelessgenie.com/blog/matrix-multiplication-recursive/#2-the-recursive-approach-fundamentals)
* [Strassen Algorithm Visually Explained](https://www.youtube.com/watch?v=2IgZuVGwEb0)
* [2.9 Strassens Matrix Multiplication](https://www.youtube.com/watch?v=0oJyNmEbS4w)


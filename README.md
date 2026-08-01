# Strassen's Matrix Multiplication

A Go implementation of Strassen's algorithm for matrix multiplication, benchmarked against the standard brute-force approach.

## Overview

Strassen's algorithm multiplies matrices in roughly O(n^2.807) time by recursively splitting matrices into quadrants and combining them with fewer multiplications than the standard O(n^3) approach. This project implements both methods in Go and times them head-to-head.

## How it works

1. An input matrix is generated (`matrix_create.go`)
2. Since Strassen's algorithm requires square matrices with power-of-2 dimensions, the matrix is padded up to the nearest power of 2 (`matrix_padding.go`, `nearest_power_of_2.go`) and reduced back down afterward (`reduce_matrix_size.go`)
3. The matrix is recursively split into quadrants (`matrix_split.go`) and combined using matrix addition/subtraction (`matrix_add.go`, `matrix_sub.go`)
4. Both the brute-force (`matrix_bruteforce.go`) and Strassen (`strassen.go`) multiplications run concurrently as goroutines
5. Execution times for both are compared (`matrix_time_compare.go`) and printed to the console

## Files

| File | Purpose |
|---|---|
| `main.go` | Entry point — runs both algorithms concurrently and prints timing results |
| `strassen.go` | Strassen's recursive matrix multiplication |
| `matrix_bruteforce.go` | Standard O(n^3) matrix multiplication for comparison |
| `matrix_create.go` | Generates matrices |
| `matrix_split.go` | Splits a matrix into 4 quadrants |
| `matrix_add.go` / `matrix_sub.go` | Matrix addition/subtraction helpers |
| `matrix_padding.go` / `nearest_power_of_2.go` | Pads matrices to the nearest power-of-2 size |
| `reduce_matrix_size.go` | Trims padded matrices back to their original size |
| `matrix_display.go` | Prints matrices to the console |
| `matrix_time_compare.go` | Compares benchmark results between the two algorithms |
| `largest_int.go` | Helper for size/dimension comparisons |
| `example_scenario.go` | Example usage scenario |

## Running it

```bash
go run .
```

This runs both the brute-force and Strassen multiplication on the same input matrix concurrently and prints how long each took.

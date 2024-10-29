# Babylonian Square Root Calculation in Assembly

This repository contains an ARM assembly implementation of the Babylonian method (also known as Heron’s method) for calculating square roots. It includes a custom division function that is used iteratively to approach the square root of a given number.

## How It Works

The Babylonian method approximates the square root of a number, \( n \), by repeatedly averaging a guess, \( x \), with \( \frac{n}{x} \) until convergence. The code consists of two main functions: `divide` and `root`.

### Key Features

#### Division Subroutine
- **Function `divide`**: Performs integer division by repeatedly subtracting the divisor from the dividend, allowing for large values and avoiding floating-point operations.
- **Overflow Prevention**: The division checks for a divide-by-zero error and handles overflow by reducing the divisor when it exceeds the dividend.

#### Babylonian Square Root Algorithm
- **Function `root`**: Implements the Babylonian method, iteratively refining the estimate \( x \) by averaging \( x \) and \( \frac{n}{x} \) until convergence.

## File Overview

### Code Structure
- **`divide`**: A division function that takes two inputs (dividend in `r1` and divisor in `r2`) and calculates the integer quotient, returning the result in `r0`.
  - **`find_power`**: Adjusts the divisor by doubling until it exceeds the dividend.
  - **`subtract`**: Performs the core division by subtraction.
  - **`update_power`**: Adjusts divisor and power for precise subtraction when divisor exceeds the current remainder.

- **`root`**: The main square root function, which uses the Babylonian method.
  - **`sqrt_loop`**: Iteratively refines \( x \) until two successive approximations are equal.

### Example Run

To calculate the square root of a number:
1. Set up an ARM emulator (such as QEMU).
2. Load the program and execute it to calculate the square root of a test value (e.g., \( n = 144 \)).

### Sample Execution:
```assembly
mov r0, #144         @ Test with n = 144
bl root              @ Calculate the square root
```

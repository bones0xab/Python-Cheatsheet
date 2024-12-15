<h1 align="center">CheatSheet</h1>
***

[Course 1 : Algorithm Comlexe](#course1)

# <a id="course1"></a> Algorithm Comlexe.
---

### **Key Points from the Document**
#### **1. Introduction**
- **Objective:** Analyze algorithm complexity in terms of time and space.
- **Key Concepts:**
  - Temporal complexity measures execution time.
  - Spatial complexity assesses memory usage.
- **Example Problem:** Given two algorithms, \( A_1 \) and \( A_2 \), select the most efficient by comparing their execution times.

---

#### **2. Methods of Complexity Measurement**
- **Experimental Method:**
  - Program the algorithm.
  - Test on datasets of varying sizes.
  - Measure execution time.
  - **Example:** Using Python's `time` module to measure execution time.
    ```python
    import time
    start = time.time()
    # Algorithm execution
    end = time.time()
    print(f"Elapsed time: {end - start} seconds")
    ```

- **Theoretical Method:**
  - Evaluate complexity through operation counts rather than runtime.
  - Define data size \( N \), identify fundamental operations, and calculate their frequency.
  - **Example:** Counting comparisons and multiplications in matrix multiplication.

---

#### **3. Common Complexities**
- **Best Case:** \( T_{\text{min}}(N) \) - Lower bound of runtime.
- **Worst Case:** \( T_{\text{max}}(N) \) - Upper bound of runtime.
- **Average Case:** \( T_{\text{avg}}(N) \) - Statistical prediction of runtime.
  - **Example:** Sequential search in an array:
    - Best Case: Element found at the start (\( O(1) \)).
    - Worst Case: Element not present (\( O(N) \)).

---

#### **4. Asymptotic Complexity**
- **Notation:**
  - \( O(f(N)) \): Upper bound.
  - \( \Omega(f(N)) \): Lower bound.
  - \( \Theta(f(N)) \): Tight bound.
- **Examples:**
  - \( T(N) = 3N^2 + 2 \) is \( O(N^2) \).
  - \( 30N + 8 \) is \( O(N) \).

---

#### **5. Master Theorem**
- Used for "Divide and Conquer" algorithms.
- Determines \( T(N) \) based on recurrence relations:
  - Case 1: \( a < b^k \Rightarrow T(N) = \Theta(N^k) \).
  - Case 2: \( a = b^k \Rightarrow T(N) = \Theta(N^k \log(N)) \).
  - Case 3: \( a > b^k \Rightarrow T(N) = \Theta(N^{\log_b a}) \).

---

#### **6. Algorithm Examples**
- **Matrix Multiplication (Theoretical Analysis):**
  - Time complexity is \( O(N^3) \) for naive implementation.
  - Example code compares `numpy.dot()` with manual nested loops.

- **Exponentiation:**
  - Iterative and recursive methods compared for performance.
  - Recursive method uses \( T(n) = 2T(n/2) + c \).

- **Search Algorithms:**
  - **Sequential Search:** Best case \( O(1) \), worst case \( O(N) \).
  - **Binary Search:** Best case \( O(1) \), worst case \( O(\log N) \).

---

#### **7. Exercises**
- Implementations and analysis for:
  - Recursive vs iterative Fibonacci.
  - Matrix multiplication optimizations.
  - Various sorting algorithms (e.g., bubble sort, quicksort).

**Example:** Recursive Fibonacci complexity:
```python
def fib_recursive(n):
    if n <= 1:
        return n
    return fib_recursive(n-1) + fib_recursive(n-2)
# Complexity: O(2^N)
```

---

### **Summary of Complexity Classes**
| Class            | Example Algorithms      | Complexity |
|------------------|-------------------------|------------|
| **Logarithmic**  | Binary Search           | \( O(\log N) \) |
| **Linear**       | Sequential Search       | \( O(N) \)      |
| **Quadratic**    | Bubble Sort             | \( O(N^2) \)    |
| **Exponential**  | Recursive Fibonacci     | \( O(2^N) \)    |

---

Let me know if you'd like detailed explanations of any specific sections or algorithms!

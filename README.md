<h1 align="center">CheatSheet</h1>

***

[Course 1 : Algorithm Comlexe](#course1)

[Course 2 : Technique Conquer and Divide](#course2)

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

***

# <a id="course2"></a> Technique divide and conquer.
---

### Summary of "Divide and Conquer (D&C)" Technique

---

### **Overview of Divide and Conquer**
- **Definition**:
  - A strategy to solve problems by:
    1. **Dividing** the problem into smaller sub-problems.
    2. **Solving** the sub-problems recursively.
    3. **Combining** the solutions to solve the original problem.
  - Sub-problems must be of the same type as the original problem.
- **Generic Algorithm**:
  ```python
  Algorithm Div_and_Conq(P, n):
      if n <= threshold:  # Base case
          return baseSol(P, n)
      subPbs = Divide(P, n)  # Divide into sub-problems
      SubSols = [Div_and_Conq(Pi, ni) for (Pi, ni) in subPbs]  # Conquer
      return Combine(SubSols)  # Combine solutions
  ```

---

### **Steps of Divide and Conquer**
1. **Divide**: Split the problem into sub-problems.
2. **Conquer**: Solve each sub-problem recursively.
3. **Combine**: Merge the solutions of sub-problems.

---

### **Analyzing D&C Complexity**
- **Master Theorem**:
  The complexity depends on:
  - \( k \): Number of sub-problems.
  - \( b \): Reduction factor for sub-problem size.
  - \( f(n) \): Cost of dividing/combining.

  Three cases for recurrence \( T(n) = kT(n/b) + f(n) \):
  1. **Case 1**: \( f(n) = O(n^c) \) where \( c < \log_b{k} \):
     - Complexity: \( O(n^{\log_b{k}}) \) (cost of solving sub-problems dominates).
  2. **Case 2**: \( f(n) = O(n^{\log_b{k}}) \):
     - Complexity: \( O(n^{\log_b{k}} \log n) \) (balanced costs).
  3. **Case 3**: \( f(n) = O(n^c) \) where \( c > \log_b{k} \):
     - Complexity: \( O(n^c) \) (cost of combining dominates).

---

### **Examples of D&C Algorithms**
#### 1. **Binary Search**
   - Divides a sorted array into two halves and searches in the relevant half.
   - **Recurrence**: \( T(n) = T(n/2) + O(1) \).
   - **Complexity**: \( O(\log n) \).
   - **Example Code**:
     ```python
     def binary_search(arr, target, low, high):
         if low > high:
             return -1
         mid = (low + high) // 2
         if arr[mid] == target:
             return mid
         elif arr[mid] > target:
             return binary_search(arr, target, low, mid - 1)
         else:
             return binary_search(arr, target, mid + 1, high)
     ```

#### 2. **Merge Sort**
   - Splits an array into halves, recursively sorts them, and merges the results.
   - **Recurrence**: \( T(n) = 2T(n/2) + O(n) \).
   - **Complexity**: \( O(n \log n) \).
   - **Example Code**:
     ```python
     def merge_sort(arr):
         if len(arr) > 1:
             mid = len(arr) // 2
             L, R = arr[:mid], arr[mid:]
             merge_sort(L)
             merge_sort(R)
             i, j, k = 0, 0, 0
             while i < len(L) and j < len(R):
                 arr[k] = L[i] if L[i] < R[j] else R[j]
                 i, j, k = (i+1, j, k+1) if L[i] < R[j] else (i, j+1, k+1)
             arr[k:] = L[i:] + R[j:]
     ```

#### 3. **Karatsuba Multiplication**
   - Multiplies large numbers by reducing the number of multiplications from 4 to 3.
   - **Recurrence**: \( T(n) = 3T(n/2) + O(n) \).
   - **Complexity**: \( O(n^{\log_2{3}}) \approx O(n^{1.58}) \).
   - **Example Code**:
     ```python
     def karatsuba(x, y):
         if x < 10 or y < 10:
             return x * y
         m = max(len(str(x)), len(str(y))) // 2
         x1, x0 = divmod(x, 10**m)
         y1, y0 = divmod(y, 10**m)
         A, B, C = karatsuba(x1, y1), karatsuba(x0, y0), karatsuba(x1 + x0, y1 + y0)
         return A * 10**(2*m) + (C - A - B) * 10**m + B
     ```

#### 4. **Matrix Multiplication**
   - Divide matrices into smaller sub-matrices, compute their products recursively, and combine results.
   - **Recurrence**: \( T(n) = 8T(n/2) + O(n^2) \).
   - **Complexity**: \( O(n^3) \) for classical D&C; \( O(n^{2.81}) \) with Strassen's algorithm.

---

### **Advantages of D&C**
- **Modularity**: Problems broken into manageable pieces.
- **Efficiency**: Reduces complexity for many problems.
- **Parallelization**: Sub-problems can often be solved independently.

### **Disadvantages**
- **Memory Overhead**: Recursive calls can use significant memory.
- **Costly Combination**: Combining solutions can be computationally expensive.

---

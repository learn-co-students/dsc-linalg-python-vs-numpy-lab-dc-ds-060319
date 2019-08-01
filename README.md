
# Pure Python vs. Numpy - Lab

## Introduction 

Numpy, Scipy and Pandas provide a significant increase in computational efficiency with complex mathematical operations as compared to Python's built in arithmetic functions. In this lab, you will calculate and compare the processing speed required for calculating a dot product using both basic arithmetic operations in Python and Numpy's `.dot()` method. 

## Objectives
You will be able to:
* Compare the performance of high-dimensional matrix operations in Numpy vs. pure Python

## Problem 

Write a routine to calculate the dot product between two $200 \times 200$ dimensional matrices using:

a) Pure Python (no libraries)

b) Numpy's `.dot()`


### Create two $200 \times 200$ matrices in Python and fill them with random values using `np.random.rand()` 


```python
# Compare 200x200 matrix-matrix multiplication speed
import numpy as np

# Set up the variables
A = None
B = None
```


```python
# __SOLUTION__ 
##### Compare 200x200 matrix-matrix multiplication speed
import numpy as np
# Set up the variables

SIZE = 200
A = np.random.rand(SIZE,SIZE)
B = np.random.rand(SIZE,SIZE)
```

## Pure Python

* Initialize a zeros-filled `numpy` matrix
* In Python, calculate the dot product using the formula 


$$ \large C_{i,j}= \sum_k A_{i,k}B_{k,j}$$


* Use Python's `timeit` library to calculate the processing time
* [Visit this link](https://www.pythoncentral.io/time-a-python-function/) for an in-depth explanation on how to time a function or routine in python

**Hint**: Use a nested for loop for accessing, calculating and storing each scalar value in the resulting matrix


```python
import timeit

# Start the timer
start = None

# Matrix multiplication in pure Python


time_spent = None

print('Pure Python Time:', time_spent, 'sec.')
```

    Pure Python Time: None sec.



```python
# __SOLUTION__ 
import timeit

# Start the timer
start = timeit.default_timer()

# Matrix multiplication in pure Python

out2 = np.zeros((SIZE,SIZE))

for i in range(SIZE):
  for j in range(SIZE):
    for k in range(SIZE):
      
        out2[i,k] += A[i,j]*B[j,k]

time_spent = timeit.default_timer() - start

print('Pure Python Time:', time_spent, 'sec.')
```

    Pure Python Time: 4.337618543067947 sec.


## Numpy 
Set the timer and calculate the time taken by `.dot()` function for multiplying $A$ and $B$ 



```python
# start the timer
start = None

# Matrix multiplication in numpy


time_spent = None
print('Numpy Time:', time_spent, 'sec.')
```

    Numpy Time: 0.0007913659792393446 sec.



```python
# __SOLUTION__ 
# start the timer
start = timeit.default_timer()

# Matrix multiplication in numpy
out1 = A.dot(B)

time_spent = timeit.default_timer() - start
print('Numpy Time:', time_spent, 'sec.')
```

    Numpy Time: 0.0006324420683085918 sec.


### Your comments


```python
# __SOLUTION__
# Your comments:

# Numpy is much faster than pure python 

# NumPy provides support for large multidimensional arrays and matrices 
# along with a collection of mathematical functions to operate on these elements. 

# Numpy relies on well-known packages implemented in other languages (like Fortran) to perform efficient computations, 
# bringing the user both the expressiveness of Python and a performance similar to MATLAB or Fortran.
```

## Summary

In this lab, you performed a quick comparison between calculating a dot product in Numpy vs Python built in function. You saw that Numpy is computationally much more efficient that Python code because of the sophisticated implementation of Numpy source code. You're encouraged to always perform time tests to fully appreciate the use of an additional library in Python. 

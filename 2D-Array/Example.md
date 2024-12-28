### 1. Creating Arrays

#### `numpy.array`

This method creates a NumPy array from a list or a nested list.

```python
import numpy as np

# Creating a 1D array
array_1d = np.array([1, 2, 3, 4, 5])

# Creating a 2D array (matrix)
array_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
```

#### `numpy.zeros`

This method creates an array filled with zeros.

```python
# Creating a 1D array of zeros
zeros_1d = np.zeros(5)

# Creating a 2D array of zeros (3x3 matrix)
zeros_2d = np.zeros((3, 3))
```

#### `numpy.ones`

This method creates an array filled with ones.

```python
# Creating a 1D array of ones
ones_1d = np.ones(5)

# Creating a 2D array of ones (3x3 matrix)
ones_2d = np.ones((3, 3))
```

#### `numpy.arange`

This method creates an array with a range of values.

```python
# Creating a 1D array with values from 0 to 9
range_array = np.arange(10)
```

#### `numpy.linspace`

This method creates an array with evenly spaced values over a specified interval.

```python
# Creating a 1D array with 5 values evenly spaced between 0 and 1
linspace_array = np.linspace(0, 1, 5)
```

### 2. Accessing Elements

#### Indexing

You can access elements using indices.

```python
# Accessing the element at row 1, column 2
element = array_2d[1, 2]
```

#### Slicing

You can slice arrays to access a range of elements.

```python
# Accessing the first row
first_row = array_2d[0, :]

# Accessing the first column
first_column = array_2d[:, 0]

# Accessing a submatrix
submatrix = array_2d[0:2, 1:3]
```

### 3. Array Operations

#### Element-wise Operations

NumPy allows you to perform element-wise operations on arrays.

```python
array_1 = np.array([1, 2, 3])
array_2 = np.array([4, 5, 6])

# Element-wise addition
sum_array = array_1 + array_2

# Element-wise multiplication
product_array = array_1 * array_2
```

#### Matrix Multiplication

You can perform matrix multiplication using the `dot` function.

```python
matrix_1 = np.array([[1, 2], [3, 4]])
matrix_2 = np.array([[5, 6], [7, 8]])

# Matrix multiplication
result_matrix = np.dot(matrix_1, matrix_2)
```

### 4. Array Methods

#### `reshape`

This method reshapes an array without changing its data.

```python
# Reshaping a 1D array to a 2D array (2x3 matrix)
reshaped_array = np.arange(6).reshape((2, 3))
```

#### `flatten`

This method flattens a multi-dimensional array into a 1D array.

```python
# Flattening a 2D array to a 1D array
flattened_array = array_2d.flatten()
```

#### `transpose`

This method transposes the array (swaps rows and columns).

```python
# Transposing a 2D array
transposed_array = array_2d.transpose()
```

### 5. Statistical Methods

NumPy provides several statistical methods to perform operations on arrays.

#### `sum`

This method calculates the sum of array elements.

```python
# Sum of all elements in the array
total_sum = array_2d.sum()

# Sum along the rows
sum_along_rows = array_2d.sum(axis=1)

# Sum along the columns
sum_along_columns = array_2d.sum(axis=0)
```

#### `mean`

This method calculates the mean (average) of array elements.

```python
# Mean of all elements in the array
mean_value = array_2d.mean()
```

#### `min` and `max`

These methods find the minimum and maximum values in the array.

```python
# Minimum value in the array
min_value = array_2d.min()

# Maximum value in the array
max_value = array_2d.max()
```



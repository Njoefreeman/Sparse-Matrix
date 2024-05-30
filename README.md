# SparseMatrix README

## Overview

The `SparseMatrix` class is a Python implementation for handling sparse matrices efficiently. A sparse matrix is a matrix in which most of the elements are zero. This class allows you to create, manipulate, and perform operations on sparse matrices while saving memory by only storing non-zero elements.

## Features

- **Initialization**: Create a sparse matrix from dimensions or a file.
- **Element Access**: Get and set elements in the matrix.
- **String Representation**: Convert the sparse matrix to a readable string format.
- **Matrix Operations**: Add, subtract, and multiply sparse matrices.

## Class Methods

### `__init__(self, numRows=None, numCols=None, matrixFilePath=None)`

Initializes a sparse matrix. You can specify the number of rows and columns or provide a file path to load the matrix from a file.

**Parameters:**
- `numRows` (int, optional): Number of rows in the matrix.
- `numCols` (int, optional): Number of columns in the matrix.
- `matrixFilePath` (str, optional): Path to a file containing the matrix data.

### `load_matrix(self, matrixFilePath)`

Loads matrix data from a file.

**Parameters:**
- `matrixFilePath` (str): Path to the file containing the matrix data.

### `parse_entry(self, entry)`

Parses a string entry from the matrix file.

**Parameters:**
- `entry` (str): A string in the format "(row,col,value)".

**Returns:**
- Tuple (int, int, int): Parsed row, column, and value.

### `get_element(self, row, col)`

Gets the element at the specified row and column. Returns 0 if the element is not explicitly stored.

**Parameters:**
- `row` (int): Row index.
- `col` (int): Column index.

**Returns:**
- `int`: Value at the specified position.

### `set_element(self, row, col, value)`

Sets the element at the specified row and column. If the value is 0, the element is removed from storage.

**Parameters:**
- `row` (int): Row index.
- `col` (int): Column index.
- `value` (int): Value to set.

### `__str__(self)`

Returns a string representation of the sparse matrix.

### `add(self, other)`

Adds two sparse matrices.

**Parameters:**
- `other` (SparseMatrix): The matrix to add.

**Returns:**
- `SparseMatrix`: Resultant matrix after addition.

### `subtract(self, other)`

Subtracts another sparse matrix from the current matrix.

**Parameters:**
- `other` (SparseMatrix): The matrix to subtract.

**Returns:**
- `SparseMatrix`: Resultant matrix after subtraction.

### `multiply(self, other)`

Multiplies the current matrix by another sparse matrix.

**Parameters:**
- `other` (SparseMatrix): The matrix to multiply with.

**Returns:**
- `SparseMatrix`: Resultant matrix after multiplication.

## Usage Example

```python
# Create a sparse matrix from a file
matrix1 = SparseMatrix(matrixFilePath="matrix1.txt")
matrix2 = SparseMatrix(matrixFilePath="matrix2.txt")

# Perform addition
result_add = matrix1.add(matrix2)
print("Addition Result:")
print(result_add)

# Perform subtraction
result_sub = matrix1.subtract(matrix2)
print("Subtraction Result:")
print(result_sub)

# Perform multiplication
result_mul = matrix1.multiply(matrix2)
print("Multiplication Result:")
print(result_mul)
```

## Main Function

The provided `main` function allows users to load two sparse matrices from files and perform an operation (addition, subtraction, or multiplication) on them. The result is printed to the console.

```python
def main():
    import os

    def load_sparse_matrix(file_path):
        return SparseMatrix(matrixFilePath=file_path)

    def perform_operation(matrix1, matrix2, operation):
        if operation == 'add':
            return matrix1.add(matrix2)
        elif operation == 'subtract':
            return matrix1.subtract(matrix2)
        elif operation == 'multiply':
            return matrix1.multiply(matrix2)
        else:
            raise ValueError("Invalid operation")

    matrix1_path = input("Enter path for first sparse matrix file: ")
    matrix2_path = input("Enter path for second sparse matrix file: ")
    operation = input("Enter the operation to perform (add, subtract, multiply): ")

    matrix1 = load_sparse_matrix(matrix1_path)
    matrix2 = load_sparse_matrix(matrix2_path)

    result = perform_operation(matrix1, matrix2, operation)
    print(result)

if __name__ == "__main__":
    main()
```

## File Format

The input file for a sparse matrix should have the following format:
```
rows=<number_of_rows>
cols=<number_of_cols>
(row,col,value)
(row,col,value)
...
```

## Installation

This class does not require any external dependencies and can be used by simply importing the class into your Python script.

```python
from sparse_matrix import SparseMatrix
```



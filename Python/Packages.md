# Numpy / Pandas

## Numpy
* ndarray: N-dimensional array type which describes a collection of “items” of the same type
```python
a = np.array([1, 2, 3])
```

## Pandas
* Serie: one-dimensional labeled indexed array based on the NumPy ndarray
* DataFrame: two-dimensional labeled data structures with columns of potentially different types
```python
s = pd.Series([1, 2, 3], index=["i1", "i2", "i3"])
d = pd.DataFrame([[1, 2, 3], [4, 5, 6]], index=["r1", "r2", "r3"], columns=["c1", "c2"])
```

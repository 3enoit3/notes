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

# Access cells
col = data["c1"]
row = data.iloc[0]
row = data.loc["r1"]
cell = data["c1"]["r1"]

for i, row in data.iterrows():
  date = row["Date"]

# Tools
data = pd.read_csv("file.csv", index_col=False) # index_col to workaround trailing ,
data.fillna(0, inplace=True) # replace NaN by 0
data.rename(columns=lambda h: h.strip(), inplace=True) # strip headers
data["Date"] = pd.to_datetime(data["Date"], format="%d/%m/%Y") # convert to date object
```

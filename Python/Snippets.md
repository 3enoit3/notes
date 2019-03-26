# Snippets
## Main
```python
import sys

def main(argv):
    return 0

if __name__ == "__main__":
    sys.exit( main(sys.argv) )
```

## File
### Append a file
```python
with open("path", "a") as file:
  file.write("data\n")
```

## Time
### Measure performances
```python
import timeit

start = timeit.default_timer()
...
end = timeit.default_timer()
print( "Completed in {0:.3f}s".format(end - start) )
```

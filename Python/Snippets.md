# Snippets
## Template
```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

"""Tool"""

import sys
import argparse
import unittest
import logging

def main():
    """Entry point"""

    # Parse options
    parser = argparse.ArgumentParser()
    parser.add_argument("-d", "--debug", action="store_true", default=False,
                        help="show debug information")
    args = parser.parse_args()

    # Configure debug
    if args.debug:
        logging.basicConfig(stream=sys.stderr, level=logging.DEBUG)
        logging.debug("Enabled debug logging")

    return 0

if __name__ == "__main__":
    sys.exit(main())

class Tests(unittest.TestCase): 
    # pylint: disable=too-many-public-methods
    """Unit tests"""
    # run test suite with 
    # python -m unittest <this_module_name_without_py_extension>

    def test(self):
        """Scenario"""
        self.assertTrue(True is True)
        self.assertEqual(True, True)
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

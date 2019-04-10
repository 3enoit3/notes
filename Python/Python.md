# Python
## Code lay-out
* Line continuation: (), {}, \[], """
  * indentation: opening delimiter or enough levels to distinguish (hanging indents)
```python
var\
="val\
ue"

var=1; var2=2
```
## Binding
* A **code block** is piece of Python program text that is executed as a unit
  * a module, a function body, a class definition, a command typed interactively
* A code block is executed in an **execution frame**
* A **scope** defines the visibility of a name within a block
  * if a local variable is defined in a block, its scope includes that block. 
  * if the definition occurs in a function block, the scope extends to any blocks contained within the defining one, unless a contained block introduces a different binding for the name. 
  * the scope of names defined in a class block is limited to the class block; it does not extend to the code blocks of methods – this includes generator expressions since they are implemented using a function scope

https://www.python.org/dev/peps/pep-0227/<br>
https://docs.python.org/2/reference/executionmodel.html#

## Scope
* Variables
  * LEGB Rule
    * **Local**: Names assigned in any way within a function (def or lambda)), and not declared global in that function.
    * **Enclosing-function** locals: Name in the local scope of any and all statically enclosing functions (def or lambda), from inner to outer.
    * **Global** (module): Names assigned at the top-level of a module file, or by executing a global statement in a def within the file.
    * **Built-in** (Python) — Names preassigned in the built-in names module : open,range,SyntaxError,...
* Functions
  * **def** is executable: it creates a function object and assigns it to a name
  * bytecode is generated during compilation as code object
```bash
> cat test.py
def f1():
    return f2()
def f2():
    return t
t = 3
print f1()

> python -m dis test.py
  1           0 LOAD_CONST               0 (<code object f1 at 0x7f34789b57b0, file "test.py", line 1>)
              3 MAKE_FUNCTION            0
              6 STORE_NAME               0 (f1)

  4           9 LOAD_CONST               1 (<code object f2 at 0x7f34789b55b0, file "test.py", line 4>)
             12 MAKE_FUNCTION            0
             15 STORE_NAME               1 (f2)

  7          18 LOAD_CONST               2 (3)
             21 STORE_NAME               2 (t)

  8          24 LOAD_NAME                0 (f1)
             27 CALL_FUNCTION            0
             30 PRINT_ITEM
             31 PRINT_NEWLINE
             32 LOAD_CONST               3 (None)
             35 RETURN_VALUE
```
[Visualize frames](http://pythontutor.com/visualize.html#code=def%20f1%28%29%3A%0A%20%20%20%20return%20f2%28%29%0Adef%20f2%28%29%3A%0A%20%20%20%20return%20t%0At%20%3D%203%0Af1%28%29&cumulative=false&curInstr=10&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false)

## Compilation
https://www.python.org/dev/peps/pep-0339/
* Source code -> Parse tree
  * LL(1) parser
* Parse tree -> Abstract Syntax Tree (AST)
  * Zephyr Abstract Syntax Definition Language (ASDL)
* AST -> Control Flow Graph (CFG)
  * creates namespaces (variables can be classified as local, free/cell for closures, or global) / symbol table
  * calculates jump offsets
* CFG -> Bytecode

## Modules
* Module
  * A file containing Python definitions and statements
  * Search path for "import XXX": XXX in built-in modules, then XXX.py in sys.path \[input script directory, PYTHONPATH, installation defaults]
  * Cache path for XXX.py: \_\_pycache__/XXX.cpython-33.pyc
```python
# Import names from a module
import module as alias; alias.f()
from module import function as falias; falias()

# Other
dir(sys)# list names defined by a module: ['__displayhook__', '__doc__', ... ]
sys.__name__ # module name: "sys"
```
* Package
  * A set of modules whose namespace uses “dotted module names” 
```python
p/
  __init__.py
  m.py
  s1/
    __init__.py
    m_s1.py
  s2/
    __init__.py
    m1_s2.py
    m2_s2.py
    
import p.s1.m_s1; p.s1.m_s1.f() # full path
from p.s1 import m_s1; m_s1.f() # module
from p.s1.m_s1 import f; f() # function
from p.s1.m_s1 import *; f() # all functions if s1/__init__.py defines __all__ = ["f"], else just the module

# In m1_s2.py
from p.s1 import m_s1
from . import m2_s2
from .. import s1
from ..s1 import m_s1
```
## Time
[Format codes](https://docs.python.org/2/library/datetime.html#strftime-and-strptime-behavior)

## Assembly
https://blog.hakril.net/articles/2-understanding-python-execution-tracer.html<br>
https://hackernoon.com/the-magic-behind-python-generator-functions-bc8eeea54220

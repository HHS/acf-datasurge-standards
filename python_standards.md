# Python Standards
- [Style Considerations](#style-considerations)
  * [Presentation](#presentation)
    + [Indentation](#indentation)
    + [Using Line spaces - Sparse is better than dense](#using-line-spaces---sparse-is-better-than-dense)
    + [Using White spaces](#using-white-spaces)
  * [Naming](#naming)
    + [Naming conventions](#naming-conventions)
  * [Program Composition](#program-composition)
    + [Comparisons, equalities, and if statements](#comparisons--equalities--and-if-statements)
    + [Lambda expressions](#lambda-expressions)
    + [Global variables and namespaces](#global-variables-and-namespaces)
    + [Imports](#imports)
    + [if __name__ == "__main__"](#if---name---------main---)
    + [Exceptions](#exceptions)
  * [Documentation](#documentation)
  * [Efficiency and Performance](#efficiency-and-performance)
- [Packages](#packages)
- [Accessibility](#accessibility)

## Style Considerations
Much of these considerations are adapted from the [PEP 8  Style Guide for Python](https://peps.python.org/pep-0008/])
### Presentation
#### Indentation
We should use 4 space indentation in our code. Ensure that your IDE is set up so that indents represent 4 spaces and not tabs. When requiring multiple lines, always align with the opening delimiter.
```{python}
# Bad:  

foo = long_function_name(var_one, var_two,  
    var_three, var_four)  

my_list = [1, 2, 3,   
    4, 5, 6,]  

# Good:  

foo = long_function_name(var_one, var_two,  
                         var_three, var_four)  

my_list = [1, 2, 3,   
           4, 5, 6,]
```
#### Using Line spaces - Sparse is better than dense
- Surround top-level function and class definitions with two blank lines.
- Method definitions inside a class are surrounded by a single blank line.
- Extra blank lines may be used (sparingly) to separate groups of related functions. Blank lines may be omitted between a bunch of related one-liners (e.g. a set of dummy implementations).
- Use blank lines in functions, sparingly, to indicate logical sections.
#### Using White spaces
Avoid extraneous whitespace in the following situations:
- Immediately inside parentheses, brackets or braces
- Between a trailing comma and a following close parenthesis
- Immediately before a comma, semicolon, or colon
- Immediately before the open parenthesis that starts the argument list of a function call
- Immediately before the open parenthesis that starts an indexing or slicing
- More than one space around an assignment (or other) operator to align it with another
  
Some examples below:
```{python}
# Good:  
spam(ham[1], {eggs: 2})  

# Bad:  
spam( ham[ 1 ], { eggs: 2 } )  

# Good:  
if x == 4: print x, y; x, y = y, x  

# Bad:  
if x == 4 : print x , y ; x , y = y , x  

# Good:  
ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]  
ham[lower:upper], ham[lower:upper:], ham[lower::step]  
ham[lower+offset : upper+offset]  
ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]  
ham[lower + offset : upper + offset]  

# Bad:  
ham[lower + offset:upper + offset]  
ham[1: 9], ham[1 :9], ham[1:9 :3]  
ham[lower : : upper]  
ham[ : upper]  

# Good:  
spam(1)  

# Bad  
spam (1)  

# Good:  
dct['key'] = lst[index]  

# Bad:  
dct ['key'] = lst [index]  

# Good  
def complex(real, imag=0.0):  
    return magic(r=real, i=imag)  

# No:  
def complex(real, imag = 0.0):  
    return magic(r = real, i = imag)

```
### Naming
There are many opinions on the best way to name variables in python. We will generally follow the guidelines in [PEP 8 - Naming Conventions](https://peps.python.org/pep-0008/#naming-conventions)
#### Naming conventions
- Variable names should be no less than 3 characters and should be ddscriptive of what the variable represents
- Use CAPITALS to define constants or globals that will be used in your entire program or module
- Use lowercase_with_underscores for local variables, member attributes or methods, function arguments and parameters
- Use PascalCase for classes
- Use short lowercase names for scripts
- Never create a variable that has __double_leading_and_trailing_underscore__

### Program Composition
#### Comparisons, equalities, and if statements
#### Lambda expressions
#### Global variables and namespaces
In Python, variable lookups go up from local namespace to parent namespace to global namespace. Below, python looks in the local namespace of multiply and cannot find GLOBALVAR so it looks in the parent scope
```{python}
GLOBALVAR = 12345  

def multiply(x):  
    return x * GLOBALVAR # GLOBALVAR = 12345
```
If you declare a variable inside a local scope, then it is immediately local unless you use the global keyword (which works at the module level)
```{python}
GLOBALVAR = 12345  

def multiply(x):  
    GLOBALVAR = 1  
    return x * GLOBALVAR # GLOBALVAR = 1  

def changeGlobal(x):  
    global GLOBALVAR        # GLOBALVAR in this scope references the global GLOBALVAR  
    GLOBALVAR = 5678        # changes GLOBALVAR  
    return x * GLOBALVAR    # GLOBALVAR = 5678  

print(GLOBALVAR)            # prints 12345  
x = multiply(2)             # x = 24690  
print(GLOBALVAR)            # prints 12345  
y = changeGlobal(2)         # y = 11356  
print(GLOBALVAR)            # prints 5678
```

#### Imports
- Imports should always be at the top of the module. Do not import a module in a class for example, unless absolutely necessary
- When importing different versions, especially in modules requiring consumption use a try block
```{python}
try:  
    import something  
except ImportError:  
    import something_else
```
Do NOT use
```{python}
from library import *
```
because it loads all top level modules of library into the global namespace

#### Exceptions
### Documentation
### Efficiency and Performance
## Packages
## Accessibility


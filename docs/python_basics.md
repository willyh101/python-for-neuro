## Episode 2 - Python Basics and Notebooks

Here we will cover how to run python code, basic syntax, and how to use Jupyter notebooks.

### Running Python Code

There are a few ways to run python code. The easiest is to use a Jupyter notebook. We'll cover that in the next section. For now, let's just run some code in the terminal.

**Whenever you run python you will need to activate your environment.** If you haven't done that yet, see the [Getting Started](getting_started.md) page.

Open a terminal and type `python`. This just starts a Python interpreter. If you type python code here, it will run it. Try it:

```python
print('Hello world!')
```

You can also run python code from a file. Create a new file called `hello_world.py` and put the same code in it. Then run it with `python hello_world.py`. You should see the same output.

### Jupyter Notebooks

Most likely, you will do the majority of you work in Jupyter Notebooks. These are interactive documents that allow you to run code and see the output. They are great for data analysis and visualization.

**As with running python code, you will need to activate your environment before starting a notebook.**

To start a notebook, open a terminal and type `jupyter notebook`. This will open a new tab in your browser. From here you can navigate to the directory where you want to create a new notebook. **Change to `./notebooks` and work out of there.** Click the `New` button in the top right and select `Python 3`. This will open a new notebook. There is also a example notebook in there you can run.

### Installing and Using Packages

Packages extend the functionality of python. You will use them extensively because pure python is not very useful for data analysis by itself.

You will need to install packages to do most of your work. The easiest way to do this is with `conda`. To install a package, open a terminal and type `conda install <package_name>`. For example, to install `numpy` type `conda install numpy`. You can also install multiple packages at once by separating them with spaces. For example, `conda install numpy pandas matplotlib`. We have already installed these packages, so you don't need to do it now.

Some python packages are not available on conda and you will need to use the `pip` package manager. To install a package with `pip`, open a terminal and type `pip install <package_name>`. For example, to install `seaborn` type `pip install seaborn`. You can also install multiple packages at once by separating them with spaces. For example, `pip install seaborn scikit-learn`. We have already installed these packages, so you don't need to do it now.

You can't run packages like scripts (most of the time), you import them into the scripts and notebooks and packages you write.

There are various ways to import a package:
    
```python
import h5py
import numpy as np
from sklearn.linear_model import LinearRegression
```


### Python Syntax

Python is a very simple language. It is easy to learn and read. Here are some of the basics.

#### Variables

Variables are assigned data using the `=` operator. For example:

```python
a = 1
b = 'hello'
```

Variables can be reassigned at any time and can change type. This is in contrast to many languages where variables are statically typed.

```python
a = 1
print(a)
a = 2
print(a)
a = 'hello'
print(a)
```

#### Data Types

Python has a few basic data types. The most common are `int`, `float`, `str`, and `bool`. You can check the type of a variable with the `type` function:

```python
type(a) 
# if you are not in a notebook, you will need to print this to the output
print(type(a))
```

Some types...

```python
a = 1 # an integer
b = 'hello' # a string
c = 2.3346 # a float
d = True # a boolean
```

#### Lists and Dictionaries

Lists and dictionaries are some more advanced data types. Lists are ordered collections of data. Dictionaries are unordered collections of data that are accessed by keys. You can create a list with `[]` and a dictionary with `{}`. For example:

```python
my_list = [1, 2, 3, 4]
my_dict = {
    'a': 1, 
    'b': 2, 
    'c': 3
}
```

To access data in lists, use numerical indexing.
    
```python
my_list[0] # returns 1
my_list[1] # returns 2
```

To access data in dictionaries, use the key.

```python
my_dict['a'] # returns 1
my_dict['b'] # returns 2
```

Note that either of these will throw an error if the index or key does not exist. Dictionaries and lists can store virtually unlimited amounts of arbitrary data (eg. they do not need to be the same type). This is in contrast to numpy arrays, which we will cover later and MATLAB matrices, which must be the same type.

#### Math

```python
# math
x1 = 1 + 3
x2 = 1 - 3
x3 = 2 * 3
x4 = 5 ** 3
x5 = 2 / 3
```
There are shortcuts to change the value of a variable itself.

```python
x = 1
x += 1 # x is now 2
x -= 1 # x is now 1
x *= 2 # x is now 2
x /= 2 # x is now 1
```

Math can do surprising and potentially useful things to different datatypes.

```python
# math with strings
a = 'hello' + 'world'
b = 'hello' * 3

# not allowed
c = 'a' + 3

# math with lists
d = [1, 2, 3] + [4, 5, 6]
```

This is why we use `numpy`! Lists do not behave like vectors or matrices.

```python
# math with numpy arrays
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
c = a + b
```

```
d = a * 3
```

#### Testing equality

```python
a = 1
b = 2
c = 1

a == b # returns False
a == c # returns True
```

The same idea works with numpy arrays, but it is implemented slightly differently.

```python
a = np.array([1, 2, 3])
b = np.array([1, 2, 3])
c = np.array([1, 2, 4])

a == b # returns array([ True,  True,  True])
a == c # returns array([ True,  True, False])
```

Note that in python `is` tests identity, not equality. This is not what you want most of the time.

```python
['a', 'b'] == ['a', 'b']
# returns True

['a', 'b'] is ['a', 'b']
# returns False

a = ['a', 'b']
b = a
a is b
# returns True

# but notably...
a = ['a', 'b']
b = ['a', 'b']
a is b
# returns False
```

#### Conditional Flow

Python has a few ways to control the flow of a program. The most common is the `if` statement. This allows you to run code if a condition is met. For example:

```python
a = 2

if a == 1:
    print('a is 1')
elif a == 2:
    print('a is 2')
else:
    print('a is not 1 or 2')
```

Note indentation is important in python. The code that is run if the condition is met must be indented. Indentitaion must be consistent throughout the code. The standard is 4 spaces, however, you can use any number of spaces as long as it is consistent. Most editors will automatically indent for you and convert tabs to spaces.

#### Loops

Loops allow you to run code multiple times. The most common loop is the `for` loop. This allows you to run code for each element in a list. For example:

```python
my_list = [1, 2, 3, 4]
for item in my_list:
    print(item)
```

You can also loop over a range of numbers. For example:

```python
for i in range(10):
    print(i)
```

Also, `while` loops are also common, but less so in data analysis. These run until a condition is met. For example:

```python
x = 10
while x > 3:
  x = x - 1
print(x)
```
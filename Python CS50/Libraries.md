### MODULES
 
A module is a file containing definition of functions, classes, variables, constants or any other Python object. Contents of this file can be made available to any other program. Python has the **import** keyword for this purpose.

```
import math 
print ("Square root of 100:", math.sqrt(100))

Output: Square root of 100: 10.0
```

```
import random

coin = random.choice(["Heads", "Tails"])
print(coin)

Output:
Heads
Heads
Tails
Tails
Tails  // and so on
```
Here, 'random' is a library/module existing somewhere created many years ago and we can access the functions, objects present inside this module. Suppose we choose a function ==choice(seq)== which takes a list of strings then on generating the output again and again, we will get a random side of coin, i.e., there is no pattern or sequence to it. We have a keyword 'from' which can be useful in accessing specific functions from a library without writing their name again and again.

```
from random import choice

coin = choice(["Heads", "Tails"])
print(coin)
```
There is another function in the 'random' module called as ==randint(a, b)==. It simply gives any random integer in between the range of values specified. 

```
import random

number = random.randint(1, 10)
print(number)

Output:
8
9
7  // And so on
```
Another function is ==shuffle(x)==, it basically shuffles a list of items and randomizes the order they are in. Suppose we have to shuffle a deck of cards.

```
import random

cards = ["Jack", "Queen", "King"]
random.shuffle(cards)
print(cards)                 // This will give output in list format only
  OR
for card in cards:
    print(card)             // This will give items one by one 
```
This shuffles does not return a singular random item like in the previous functions. But rather gives the entire list with shuffled or randomized items.
Similar to 'random', there is a variety of modules in Python. One of them is 'statistics'. We have a bunch of functions inside this module like ==mean==.

```
import statistics

print(statistics.mean([100,90]))

Output: 95                      // Average of numbers 100 and 90
```

**COMMAND-LINE ARGUMENTS**

Command-line arguments are simply inputs we give to our program when we run it from the terminal(command-line) instead of typing input inside the program.
Instead of writing this :
```
name = input("Enter your name: ")

Output: 
Enter your name: Jack
```
We do this :
```
python program_name.py Jack
```
To use these arguments, Python uses a built-in module called 'sys'.

```
import sys

print(sys.argv)
```
If we run : 
```
python program_name.py Jack

Output will be:
['program_name.py', 'Jack']
```
==sys.argv== is a list and and first element of this list sys.argv[0] is the filename. Rest of the elements are the actual arguments. Example, Taking a name.

```
import sys

name = sys.argv[1]
print("Hello", name)

python program_name.py Jack

Output: Hello Jack
```
Suppose we do not give any name in the terminal as input. Then an exception will be raised or rather an error will occur called as IndexError.

```
import sys
print("Hello", sys.argv([1]))

Output: 
IndexError: list index out of range 
```
This essentially implies that there is nothing present at index 1 in the list. For this we can use the try and except keywords to catch such errors.

```
import sys

try:
   print("Hello", sys.argv([1]))
except IndexError:
   print("Too few arguments")
```
We can do this using if-else conditionals as well.

```
import sys

if len(sys.argv) < 2:
   print("Too few arguments")
elif len(sys.argv) > 2:
   print("Too many arguments")
else:
   print("Hello", sys.argv([1]))
```
Now, we have a response for every case whether it be no argument, too many or less arguments. Suppose someone wants their full name to be displayed but upon giving both the first and the last names, the compiler will take them as individual values inside the list and will display the 'too many arguments' message. To tackle this, we can simply enclose the full name inside double quotes.

```
python program_name.py "Jack Russell"
Hello Jack Russell
```
Suppose we want to remove the else part from our program just to separate the error handling part and the printing name part. Then we increase the possibility of raising an exception.

```
import sys

// Error Handling
if len(sys.argv) < 2:
   print("Too few arguments")
elif len(sys.argv) > 2:
   print("Too many arguments")

// Printing Name tags
print("Hello", sys.argv([1]))
```

```
python program_name.py
Too few arguments

IndexError: list out of range
```
Due to the user not giving the required data, we are now printing the cause of not producing the output but we have also encountered an error which is element not present at index 1. To handle this, we have another sys module function ==sys.exit==, which will happen the program to exit at that line then and there.

```
import sys

if len(sys.argv) < 2:
   sys.exit("Too few arguments")
elif len(sys.argv) > 2:
   sys.exit("Too many arguments")

print("Hello", sys.argv([1]))
```
Now even in case of no argument or less arguments, the program will not try to print the contents of the list and therefore no exception will be raised.

```
python program_name.py 
Too few arguments
```
Suppose we want to have slices of the input provided, that is, there are more than one words in the input and we want to print those words separately.

```
import sys

if len(sys.argv) < 2:
   sys.exit("Too few arguments")

for arg in sys.argv[1:]:
   print("Hello ", arg)                       // arg is a variable 
```

```
python program_name.py Jack Russell Croix
Hello Jack
Hello Russell
Hello Croix
```
We can give various types of combinations of indices in the for loop.

```
import sys

if len(sys.argv) < 2:
   sys.exit("Too few arguments")

for arg in sys.argv[1:-1]:
   print("Hello ", arg) 

python program_name.py Jack Russell Croix
Hello Jack
Hello Russell                      
```
Now we have just uninvited Croix from the printing part of the output. So, if we give we a negative number it has the effect of counting from the other direction, i.e., from the end of the list.
#### PYTHON BUILT-IN MODULES

Python's standard library comes bundled with a large number of modules. They are called built-in modules. Most of these built-in modules are written in C (as the reference implementation of Python is in C), and pre-compiled into the library. These modules pack useful functionality like system-specific OS management, disk IO, networking, etc.

| S.No. | Name & Description                                                                                                                                                                 |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | os : This module provides a unified interface to a number of operating system functions.                                                                                           |
| 2.    | string : This module contains a number of functions for string processing.                                                                                                         |
| 3.    | re : This module provides a set of powerful regular expression facilities. Regular expression (RegEx), allows powerful string search and matching for a pattern in a string.       |
| 4.    | math : This module implements a number of mathematical operations for floating point numbers. These functions are generally thin wrappers around the platform C library functions. |
| 5.    | cmath : This module contains a number of mathematical operations for complex numbers.                                                                                              |
| 6.    | datetime : This module provides functions to deal with dates and the time within a day. It wraps the C runtime library.                                                            |
| 7.    | gc : This module provides an interface to the built-in garbage collector.                                                                                                          |
and many more on Python Modules article by tutorialspoint.

#### PYTHON USER-DEFINED MODULES

Any text file with **.py** extension and containing Python code is basically a module. It can contain definitions of one or more functions, variables, constants as well as classes. Any Python object from a module can be made available to interpreter session or another Python script by import statement. A module can also include runnable code.

**Creating a Module**
Creating a module is nothing but saving a Python code with the help of any editor. Let us save the following code as mymodule.py

```
def SayHello(name): 
   print ("Hi {}! How are you?".format(name)) 
   return
```
We can now import mymodule in the current Python terminal.

```
>>> import mymodule 
>>> mymodule.SayHello("Harish") 
Hi Harish! How are you?
```

We can also import one module in another Python script. Save the following code as example.py.

```
import mymodule 
mymodule.SayHello("Harish")
```
Run this script from command terminal.

```
Hi Harish! How are you?
```

In Python, the import keyword has been provided to load a Python object from one module. The object may be a function, class, a variable etc. If a module contains multiple definitions, all of them will be loaded in the namespace.
Let us save the following code having three functions as mymodule.py.

```
def sum(x,y): 
   return x+y 
def average(x,y): 
   return (x+y)/2 
def power(x,y): 
   return x**y
```
The ==import mymodule== statement loads all the functions in this module in the current namespace. Each function in the imported module is an attribute of this module object. To call any function, use the module object's reference. For example, mymodule.sum().

```
import mymodule 
print ("sum:",mymodule.sum(10,20)) 
print ("average:",mymodule.average(10,20)) 
print ("power:",mymodule.power(10, 2))

Output:
sum:30
average:15.0
power:100
```

To import specific functions from mymodule.py, we use this syntax.

```
from mymodule import sum, average 
print ("sum:",sum(10,20)) 
print ("average:",average(10,20))

Output: 
sum: 30
average: 15.0
```
Note that function need not be called by prefixing name of its module to it.
We can also use ==from mymodule import* ==to import all functions without writing their names one by one.
We can also assign an alias to a long module name.

```
import mymodule as x 
print ("sum:",x.sum(10,20)) 
print ("average:", x.average(10,20)) 
print ("power:", x.power(10, 2))
```

### PACKAGES

A package is just a folder that contains multiple Python files(modules). Think of it like this- 
a library is a package and the books inside it are the different modules in Python.
PyPI is a Python Package Index, simply put it is an App Store for Python packages/modules.
**Example packages on PyPI**:
- `numpy` → math operations
- `pandas` → data analysis
- `requests` → HTTP requests
- `flask` → web apps
How to install packages from PyPI?
```
pip install numpy
```
Now, we can simply import the package inside our Editor.
We have 'cowsay', another fun Python package that prints messages with a talking cow.

```
import cowsay

cowsay.cow("Hello Jack")
   OR

import cowsay
import sys

if len(sys.argv) == 2:
   cowsay.cow("Hello "+ sys.argv[1])
```

```
Output:
 _____________
< Hello Jack >
 -------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```
We have another function inside the 'cowsay' package, ==cowsay.trex==. It can be used to print messages printed by a literal T-Rex (dinosaur).

```
import cowsay
import sys

if len(sys.argv) == 2:
   cowsay.trex("Hello "+ sys.argv[1])
```
We can simply run this inside our VS Code IDE. 
Now, we understand another python package which is ==requests==. requests is used to send HTTP requests to websites. Simply saying, it lets our Python code talk to the internet.
- `requests.get()` → sends a request to a website
- `response` → what the website sends back

```
import requests
import sys

if len(sys.argv) != 2:
   sys.exit()
response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
print(response.json())
```
.json() ensures that the data we are getting back on our screen is formatted exactly as that. Here, our program searches for a song related to the word input on the terminal then sends a request to Apple iTunes API using 'requests'. We get a JSON response from the API and we get a song name, album details like date of release and so on in dictionary format.
Now if we want to format our data more cleanly and in a readable format, we can use a library called ==json== which comes installed with Python.
```
import json
import requests
import sys

if len(sys.argv) != 2:
   sys.exit()
response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
print(json.dumps(response.json(), indent=2))
```

```
import json
import requests
import sys

if len(sys.argv) != 2:
   sys.exit()
response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
o = response.json()
for result in o["results"]:
    print(result["trackName"])
```
Here, we have read the previous output and know that we only want the song names to be displayed so we will traverse the output and get only track names using the key 'results'. We can also change the limit and give 50 as the parameter inside the link to get more than one song name.
```
def main():
    hello("world")
    goodbye("world")

def hello(name):
    print(f"Hello, {name}")

def goodbye(name):
    print(f"goodbye, {name}")

main()
```

```
python sayings.py
Hello, world
goodbye, world
```
Now, we want to use our user defined library in another program. So we create a program say.py importing the function hello from module sayings. But on giving the name David on the CLI, we get the sayings.py output as well along with Hello, David.

```
import sys
from sayings import hello

if len(sys.argv) == 2:
    hello(sys.argv[1])
```

```
Hello, world
goodbye, world
Hello, David
```
Here the problem is that on calling/importing hello function from sayings.py it reads the entire program inside the module and main() is being called at the end of the file and so the program inside say.py also ends up calling main() which results in above output. For this, write the program inside sayings.py like this.

```
def main():
    hello("world")
    goodbye("world")

def hello(name):
    print(f"Hello, {name}")

def goodbye(name):
    print(f"goodbye, {name}")

if __name__ == "__main__":
    main()
```
This __name__ is a special variable in Python whose value is automatically set to this __ main __ when we run a file on Command Line. This condition checks "Is this file being run directly, or is it being imported into another file?". When we run the file sayings.py directly, the condition becomes True and therefore both hello and goodbye statements are printed. But when we import this file into another, the condition becomes False and so only the imported function is considered.
### PACKING & UNPACKING IN PYTHON

- **Packing** = putting many items into one bag
- **Unpacking** = taking items out of the bag
That’s exactly what Python does with values.

Packing = putting multiple values into one variable.
```
numbers = 1, 2, 3
print(numbers)

Output: (1, 2, 3)
```
Python automatically packs values into a tuple.

Unpacking = taking values out into separate variables.
```
numbers = (1, 2, 3)
a, b, c = numbers

print(a)
print(b)
print(c)

Output:
1
2
3
```

Asterisk helps when number of values are more than number of variables.

```
nums = (10, 20, 30, 40)
a, *b = nums

print(a)
print(b)

Output:
10
[20, 30, 40]  // *b collects remaining values as a list
```

#### PACKING IN FUNCTIONS(*args)

When we do not know how many inputs will come.
```
def add_all(*nums):
    print(nums)

add_all(1, 2, 3)

Output: (1, 2, 3)  // All values are packed into a tuple
```

#### PACKING WITH KEYWORDS(** kwargs)

Stores data as dictionary.
```
def show_info(**data):
    print(data)

show_info(name="Aisha", age=20)

Output: {'name': 'Aisha', 'age': 20}
```

#### UNPACKING IN FUNCTIONS

Sending list values separately.
```
def add(a, b, c):
    print(a + b + c)

nums = [1, 2, 3]
add(*nums)

// Same as
add(1, 2, 3)
```

#### UNPACKING DICTIONARY

```
def show(name, age):
    print(name, age)

info = {"name": "Aisha", "age": 20}
show(**info)
```

**QUICK SUMMARY**

| Concept   | Meaning                               |
| --------- | ------------------------------------- |
| Packing   | Combine values into one variable.     |
| Unpacking | Break values into multiple variables. |
| * args    | Pack multiple values into tuple.      |
| ** kwargs | Pack key-value pairs(dictionary).     |
| *         | Unpack list/tuple.                    |
| **        | Unpack Dictionary.                    |

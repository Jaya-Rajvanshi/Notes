
We want to get return value after giving input in a Python program.

```
name = input("What is your name? ")    
print("Hello, name")
```

But this will not give us the required output in the form of "Hello, David". It will still look like "Hello, name". So what should be our approach? We need the program to take the name input by the user and then give the output alongside 'Hello'. 

```
name = input("What is your name? ")    
print("Hello, ")
print(name)
```

Output :                            Now this is not a perfect solution or correct grammatically 
Hello,                                 but it works mostly. At least we are getting output of  
David                                 input by the user.

```
name = input("What is your name? ")    
print("Hello," + name)    OR    print("Hello,", name)
```
Now it will give "Hello, David".

```
print(*objects, sep ='  ',  end = '\n' , file = sys.stdout, flush = False)
```
Here, *objects* implies that print function takes objects of any data type. *sep* is a value providing blank space between texts and *end* tells the code to go to new line. Now we will see how we can use these to improve our program.

```
print("Hello, ", end = "")
print(name)

Output : Hello, David
```

```
print("Hello, ", end = "??")
print(name)

Output : Hello, ??David
```

```
print("Hello, ", name, sep = "??")

Output : Same result as before
```

Or we could simply do this. But there are various ways of implementing even a single line of text.
```
print("Hello, ", name)

Output : Hello, David
```

```
print("Hello, \"friend\"")  //This is Escaping
OR 
print('Hello, "friend" ')
```

Now we will see what is Format String and how to implement it. Format String tells the system that we want to format our string in a special way.

```
print(f"Hello, {name}")
```

### String Functions

- strip() : Removes whitespace from string.

   ```
   name = name.strip()
   print(f"Hello, {name}")
   ```
   
   This will give normal amount of whitespace in the output before the name input by the user regardless of how many whitespaces were given during input.

- capitalize() : Capitalize the first letter of the first word of string.

  ```
  name = name.capitalize()
  ```

- title() : Capitalizes the first letter of each word of a string.

 ```
name = name.title()
 ```

Now we will optimize our whole code so that it takes less time and space.

```
name = input("What is your name? ").strip().title()    //Optimized Code
print(f"Hello, {name}")
```

- split() : Split words into two parts of a strings or we can say for this case, split() method splits user's name into first name and last name.

```
first, last = name.split(" ")
print(f"Hello, {first}")

Output : Hello, David Malan
```

We know Python like other programming languages work with data types and operators. Therefore, we will try to create a simple calculator.

### Calculator

```
x = input("What is x? ")
y = input("What is y? ")
z = x + y                          //This will not do addition of 
print(z)                           //the values of x and y
```
Here, '+' works as concatenation of the string values and not an arithmetic operator. Now we will try to fix this. This bug happens due to the fact that x and y are not recognized as integers. In Python, ==int== acts as a data type as well as a function. 

```
x = input("What is x? ")
y = input("What is y? ")
z = int(x) + int(y)
print(z)

Output : What is x? 3
         What is y? 4
         7
```
We can also give values of x and y as integer directly without the need of third var z.

```
x = int(input("What is x? "))
y = int(input("What is y? "))
print(x + y)
```

 In the first method even if the user inputs something other than an integer value it will still be accepted. But that is not the case with the second method. For now, both are good and we will deal with user input errors later.
 Now, we will look at another data type that is ==float==.

```
x = float(input("What is x? "))
y = float(input("What is y? "))
print(x + y)
```
But suppose we only want to round off the output value to float value. For this there is a method/function called as 'round'.

```
round(number[, ndigits])
```
ndigits tells up to which place we want to round off our number that is tens place, hundreds and so on.

```
x = float(input("What is x? "))
y = float(input("What is y? "))
z = round( x + y )                  //It will simply round off to  
print(z)                            //nearest integer at ones place
```
To format large numbers with commas and period, we have a particular syntax.

```
print(f"{z : ,}")

Output :
What is x? 999
What is y? 1
1,000
```

```
x = float(input("What is x? "))
y = float(input("What is y? "))
z = x/y
print(z)

Output : 
What is x? 2
What is y? 3
0.66666666666666
```

```
z = round(x/y, 2)               //We can round off the value of 
print(z)                        //to 2 decimal places

Output :
What is x? 2
What is y? 3
0.67
```

```
z = x/y
print(f"{z : .2f"})              //Same Output
```

### Functions

A Python function is a block of organized, reusable code that is used to perform a single, related action. Functions provide better modularity for our application and a high degree of code reusing.  A Python function may be invoked from any other function by passing required data (called **parameters** or **arguments**). The called function returns its result back to the calling environment.

#### Types of Python Functions

| S.No. | Type & Description                                                                                                                                                                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | Built - in Functions :  Python's standard library includes number of built-in functions. Some of Python's built-in functions are print(), int(), len(), sum(), etc. These functions are always available, as they are loaded into computer's memory as soon as we start Python interpreter. |
| 2.    | Functions defined in built - in modules : The standard library also bundles a number of modules. Each module defines a group of functions. These functions are not readily available. We need to import them into the memory from their respective modules.                                 |
| 3.    | User - defined Functions : In addition to the built-in functions and functions in the built-in modules, we can also create your own functions. These functions are called user-defined functions.                                                                                           |
#### Defining a Python Function

We can define custom functions to provide the required functionality. Here are simple rules to define a function in Python −
- Function blocks begin with the keyword def followed by the function name and parentheses ().
- Any input parameters or arguments should be placed within these parentheses. We can also define parameters inside these parentheses.
- The code block within every function starts with a colon (:) and is indented.
- The statement return (expression) exits a function, optionally passing back an expression to the caller. A return statement with no arguments is the same as return None.

#### ##Syntax 
```
def function_name( parameters ): 
   "function_docstring" 
    function_suite 
    return [expression]
```
By default, parameters have a positional behavior and we need to inform them in the same order that they were defined.
Now, we want to create our own custom functions rather than manually writing the same piece of code again and again.

```
def greetings(): 
    "This is docstring of greetings function" 
    print ("Hello World") 
    return
```

![[Pasted image 20260324141645.png]]
Python uses pass by reference mechanism. As variable in Python is a label or reference to the object in the memory, both the variables used as actual argument as well as formal arguments really refer to the same object in the memory. We can verify this fact by checking the id() of the passed variable before and after passing.

```
def testfunction(arg): 
    print ("ID inside the function:", id(arg)) 
var = "Hello" 
print ("ID before passing:", id(var)) 
testfunction(var)

Output:
ID before passing: 1996838294128
ID inside the function: 1996838294128
```
The behavior also depends on whether the passed object is mutable or immutable. Python numeric object is immutable. When a numeric object is passed, and then the function changes the value of the formal argument, it actually creates a new object in the memory, leaving the original variable unchanged.

```
def hello(to) :
    print("Hello,",to)

name = input("What is your name? ")
hello(name)
```
We have created our own hello function that allows us to say hello to anyone with a name. We can also give default value to function parameter just in case the programmer wants to say hello to everyone.

```
def hello(to = "world") :
    print("Hello,",to)

name = input("What is your name? ")
hello(name)
```

**IMP** If we use a function in Python it should already exist by the time we call it.

**SCOPE :**  refers to a variable only existing in the context in which we defined it.

```
def main():
    name = input("What is your name? ")
    hello()                        //It should be hello(name)

def hello():                       //It should be written like
    print("Hello,", name)          //print("Hello,", to)

main()

Output : 
What is your name? David
NameError : name 'name' not defined
```

A program that returns the square of a value. We will use ==return== keyword here for the first time.

```
def main():
   x = int(input("What is x? "))
   print("x squared is ", square(x))

def square(n):
   return n * n                   //n ** 2 OR pow(n, 2)
   
main()
```

#### Different Types of Function Arguments

1. Default Arguments : If we don't pass a value, it uses default value. Parameters are optional.
```
def greet(name, age=18):
    print(name, age)

greet("Aisha")      # age = 18 (default)
greet("Aisha", 21)  # age = 21
```

2. Positional Arguments : Values are assigned based on order (position). Order matters here.
```
def greet(name, age):
    print(name, age)

greet("Aisha", 20)  # Aisha 20

greet(20, "Aisha")  # Wrong meaning
```

3. Keyword Arguments : We specify which value goes to which parameter. Order does not matter here.
```
def greet(name, age):
    print(name, age)

greet(age=20, name="Aisha")
```

4. Positional-Only Arguments : Must be passed only by position, and not by keywords. Use ==/== in function parameters. Useful when we don’t want users to use parameter names.
```
def greet(name, /):
    print(name)

greet("Aisha")        # ✅
# greet(name="Aisha") ❌ Error
```

5. Keyword-Only Arguments : Must be passed using only keywords. Use * in Function definition. Forces clarity.
```
def greet(*, name):
    print(name)

greet(name="Aisha")   # ✅
# greet("Aisha")      ❌ Error
```

6. Arbitrary or Variable-length Arguments : 
    (a) * args - Multiple positional arguments. Accepts many values as tuple.
    ```
    def add(*numbers):
       print(numbers)

    add(1, 2, 3)
    
    Output:
    1, 2, 3
    ```

    (b) ** kwargs - Multiple keyword arguments. Accepts many key-value pairs as dictionary.
 ```
   def details(**info):
      print(info)

   details(name="Aisha", age=20)  
   
   Output: {'name': 'Aisha', 'age': 20}
 ```


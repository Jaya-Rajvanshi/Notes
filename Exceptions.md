An exception is an event, which occurs during the execution of a program that disrupts the normal flow of the program's instructions. In general, when a Python script encounters a situation that it cannot cope with, it raises an exception. An exception is a Python object that represents an error.

When a Python script raises an exception, it must either handle the exception immediately otherwise it terminates and quits.
If we have some suspicious code that may raise an exception, we can defend our program by placing the suspicious code in a **try**: block. After the **try**: block, include an **except**: statement, followed by a block of code which handles the problem as elegantly as possible.

```
x = int(input("What is x? "))
print(f"x is {x}")
```
Now in the above code, if user types in an input that is integer either positive or negative, then all is good. But the second user types in something like a string as input, the interpreter will give an error message. To handle errors/exceptions, we have a keyword called 'try'.

```
try:
   x = int(input("What is x? "))
   print(f"x is {x}")
except ValueError:
   print("x is not an integer")
```
Now it will give the message written in the except block if user inputs something other than an integer.

- The **try**: block contains statements which are susceptible for exception
- If exception occurs, the program jumps to the **except**: block.
- If no exception in the **try**: block, the **except**: block is skipped.

```
try: 
   x = int(input("What is x? "))
except ValueError:
   print("x is not an integer")
print(f"x is {x}")
```
This gives an error NameError: x is not defined. Here, in case the input was not an integer, the control will go directly to except part of the code. So, assignment to x never happened and therefore, when print statement tries to access x it does not exist in memory. Simply put, if an exception happens, Python skips the rest of the try block - including variable assignment. So any variable defined inside try may not exist outside it unless the operation succeeds. 
For this, there is another keyword used in Python alongside try-except, which is 'else'.

```
try: 
   x = int(input("What is x? "))
except ValueError:
   print("x is not an integer")
else:                           // In the case, nothing goes wrong.
   print(f"x is {x}")
```
There is another way of writing this code.

```
while True:
   try: 
      x = int(input("What is x? "))
   except ValueError:
      print("x is not an integer")
   else:                           // In the case, nothing goes wrong.
      break
print(f"x is {x}")
```

```
Output:
What is x? cat
x is not an integer
What is x?
```
Notice that due to adding while loop, the code is not terminated even after the user inputs a non integer value but rather the system prompts the user by asking him to enter the value of x. This tackles our problem of exception handling, user input and also reduces the need to run the program again and again. We break out of the while loop once the user has cooperated and entered an integer value.
Some might think why we have used 'break' here and not simply written our second print statement in its place. This is because such a program will create an infinite loop even if the user cooperates and gives an integer input.

```
while True:
   try: 
      x = int(input("What is x? "))
   except ValueError:
      print("x is not an integer")
   else:                           // In the case, nothing goes wrong.
      print(f"x is {x}")
```

```
Output:
What is x? 50
x is 50
What is x? 56
x is 56 
What is x? // and so on it will continue to run
```
We can implement this program using functions as well.

```
def main():
   x = get_int()
   print(f"x is {x}")
def get_int():
   while True:
      try: 
         x = int(input("What is x? "))
      except ValueError:
         print("x is not an integer")
      else:                           
         return x
main()
```
Here, we have used 'return' in place of break since it is stronger of the two and it breaks out of the loop as well as returns whatever integer value is required by the programmer whereas with break we have to write a return statement separately outside the control flow.
We can refine this program further by removing the else statement part. But some might argue that such a program may not be as beginner friendly and readable as previous versions.

```
def main():
   x = get_int()
   print(f"x is {x}")
def get_int():
   while True:
      try: 
         return int(input("What is x? "))
      except ValueError:
         print("x is not an integer")
    
main()
```
Now, suppose instead of reminding the user again and again that he has provided the wrong input like a text input, we just want to ignore the exception and prompt the user to just input an integer value, we can use 'pass' statement/keyword for this.

```
def main():
   x = get_int()
   print(f"x is {x}")
def get_int():
   while True:
      try: 
         return int(input("What is x? "))
      except ValueError:
         pass
    
main()
```

```
Output:
What is x? tiger
What is x? dog
What is x? 78
x is 78
```
So it will keep on just prompting the user to input the value without telling them the exception/error. This may be more user friendly but can be confusing for some as well in the event that users want to know the reason for the continuous prompting. So argument can be made both ways and in the end it depends entirely upon the programmer.
Another version of the program can be implemented.

```
def main():
   x = get_int("What is x? ")
   print(f"x is {x}")

def get_int(prompt):
   while True:
      try: 
         return int(input(prompt))
      except ValueError:
         pass
    
main()
```
There is another keyword 'raise' in Python which helps the programmers to raise exceptions themselves. But we will look at it later.

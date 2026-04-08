Python loops allow us to execute a statement or group of statements multiple times.
In general, statements are executed sequentially: The first statement in a function is executed first, followed by the second, and so on. There may be a situation when you need to execute a block of code several number of times.
Programming languages provide various control structures that allow for more complicated execution paths.

### Types of Loops in Python

**while loop :**  Repeats a statement or group of statements while a given condition is TRUE. It tests the condition before executing the loop body

**for loop :**  Executes a sequence of statements multiple times and abbreviates the code that manages the loop variable.

**Nested loops :** You can use one or more loop inside any another while, for or do..while loop.

### Python Loop Control Statements 

Loop control statements change execution from its normal sequence. When execution leaves a scope, all automatic objects that were created in that scope are destroyed.

Python supports the following control statements. Let us go through the loop control statements briefly.

**break :** Terminates the loop statement and transfers execution to the statement immediately following the loop.

**continue :**  Causes the loop to skip the remainder of its body and immediately retest its condition prior to reiterating.

**pass :** The pass statement in Python is used when a statement is required syntactically but you do not want any command or code to execute.

**IMPORTANT**
Unlike languages like C,CPP.. we can use **else** for loops. When the loop condition of "for" or "while" statement fails then code part in "else" is executed. If a **break** statement is executed inside the for loop then the "else" part is skipped. Note that the "else" part is executed even if there is a **continue** statement.

### ## Syntax of Python for Loop

```
for iterating_var in sequence: 
     statement(s)
```
Here, the iterating_var is a variable to which the value of each sequence item will be assigned during each iterations.  Statements represents the block of code that you want to execute repeatedly.

Before the loop starts, the sequence is evaluated. If it's a list, the expression list (if any) is evaluated first. Then, the first item (at index 0) in the sequence is assigned to iterating_var variable.

During each iteration, the block of statements is executed with the current value of iterating_var. After that, the next item in the sequence is assigned to iterating_var, and the loop continues until the entire sequence is exhausted.

![[Pasted image 20260312112132.png]]

###  Python for Loop with Strings

A string is a sequence of letters, each having a positional index. Since, it is a sequence, you can iterate over its characters using the for loop.
We write a program that compares each character in a string and displays if it is not a vowel.

```
zen = "Beautiful is better than ugly. Explicit is better than implicit. Simple is better than complex. Complex is better than complicated. " 
for char in zen: 
   if char not in 'aeiou': 
      print (char, end='')
```

### Python for Loop with Tuples

Python's tuple object is also an indexed sequence, and hence we can traverse its items with a for loop.
We write a program using for loop that traverses a tuple containing integers and returns the total of all numbers.

```
numbers = (34,54,67,21,78,97,45,44,80,19) 
total = 0 
for num in numbers: 
    total += num 
print ("Total =", total)
```

==Difference between Tuple and List==
The core difference between a **tuple** and a **list** in programming (specifically in Python, where they are primary data structures) is that ==**lists are mutable** (changeable) while **tuples are immutable** (unchangeable)==.

| List                                                                              | Tuple                                                                                            |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Mutable (elements can be added, removed, or changed after creation)               | Immutable (cannot be changed after creation)                                                     |
| Uses square brackets `[]`                                                         | Uses parentheses `()` (parentheses are optional, but recommended for clarity)                    |
| Slightly slower due to the overhead of dynamic resizing and modification.         | Generally faster to access and iterate over due to a fixed, optimized size and memory allocation |
| Consumes more memory as extra space is pre-allocated for future changes           | More memory-efficient as only the necessary memory is allocated at creation.                     |
| Many methods available for modification (e.g., append(), remove(), sort(), pop(). | Limited methods, mostly for counting and indexing (e.g., count(), index().                       |
| Cannot be used as dictionary keys because they are mutable and unhashable         | Can be used as dictionary keys because they are mutable and unhashable                           |
### Python for Loop with Lists

Python's List object is also an indexed sequence, and hence you can iterate over its items using a for loop.
In the following example, the for loop traverses a list containing integers and prints only those which are divisible by 2.
```
numbers = [32, 54, 67, 31, 78, 97, 45,44,80,19]
total = 0
for num in numbers :
   if num % 2 == 0:
      print(num)
```

```
students = ["Harry", "Hermione", "Ron"]
print(students[0])
print(students[1])
print(students[2])
```
But this may be tedious and time consuming to write when we have large number of values or strings in a list. Therefore, we will use for loop.

```
students = ["Harry", "Hermione", "Ron"]
for student in students:
  print(student)
```

```
students = ["Harry", "Hermione", "Ron"]
for i in range(len(students)):
  print(i, students[i])
  
Output:
0 Harry
1 Hermione
2 Ron
```

### Python for Loop with Range Objects

Python's built-in range() function returns an iterator object that streams a sequence of numbers. This object contains integers from start to stop, separated by step parameter. We can run a for loop with range as well.

```
range(start, stop, step)
```
- **Start** − Starting value of the range. Optional. Default is 0
- **Stop** − The range goes up to stop-1
- **Step** − Integers in the range increment by the step value. Option, default is 1.

```
for num in range(5): 
   print (num, end=' ') 
print() 
for num in range(10, 20): 
   print (num, end=' ') 
print() 
for num in range(1, 10, 2): 
   print (num, end=' ')
```

```
for i in [0,1,2]:
  print("meow")
// This will print "meow" 3 times 
```
Rather than using 'range' here, we have simply given a list of values for i in the loop. For each of the values 0, 1, 2, meow will be printed. But for a long list of values of i, we cannot write the list every time. Therefore, we require 'range'.

```
for i in range(3):
  print("meow")
```

```
print("meow\n" * 3, end ="")
```
All these will give same output of meow printed 3 times.
### Using else Statement with for Loop

Python supports to have an else statement associated with a loop statement. However, the else statement is executed when the loop has exhausted iterating the list.
The following example illustrates the combination of an else statement with a for statement that searches for prime numbers from 10 to 20.

```
//For loop to iterate between 10 to 20 
for num in range(10, 20): 
    //For loop to iterate on the factors 
    for i in range(2, num): 
       //If statement to determine the first factor 
       if num % i == 0: 
         //To calculate the second factor
          j = num/i 
          print ("%d equals %d * %d" % (num, i, j)) 
          //To move to the next number 
          break 
       else: 
          print (num, "is a prime number") 
          break
```

```
Output :
10 equals 2 * 5
11 is a prime number
12 equals 2 * 6
13 is a prime number
14 equals 2 * 7
15 equals 3 * 5
16 equals 2 * 8
17 is a prime number
18 equals 2 * 9
19 is a prime number
```

### Using For-else with & without break Statement

```
for i in ['T', 'P']: 
  print(i) 
else: 
  // Loop else statement 
  // there is no break statement in for loop, hence else part gets executed      directly 
  print("ForLoop-else statement successfully executed")
  
Output: 
T
P
ForLoop-else statement successfully executed
```

```
for i in ['T','P']: 
  print(i) 
  break 
else: 
  // Loop else statement 
  // terminated after 1st iteration due to break statement in for loop        print("Loop-else statement successfully executed")
  
Output:
T
```

### ## Syntax of while Loop

A while loop in Python programming language repeatedly executes a target statement as long as the specified boolean expression is true. This loop starts with while keyword followed by a boolean expression and colon symbol (:). Then, an indented block of statements starts.
Here, statement(s) may be a single statement or a block of statements with uniform indent. The condition may be any expression, and true is any non-zero value. As soon as the expression becomes false, the program control passes to the line immediately following the loop.
If it fails to turn false, the loop continues to run, and doesn't stop unless forcefully stopped. Such a loop is called infinite loop, which is undesired in a computer program.

```
while expression: 
   statement(s)
```
Python uses indentation as its method of grouping statements.

```
count=0 
while count<5: 
   count+=1 
   print ("Iteration no. {}".format(count)) OR
   print ("Iteration no. ",count)
   
print ("End of while loop")

Output:
Iteration no. 1
Iteration no. 2
Iteration no. 3
Iteration no. 4
Iteration no. 5
End of while loop
```

```
i = 0
while i < 3:
  print("meow")
  i += 1           //We cannot write i++ or i-- in Python
```
**IMP**
Python does not have unary operators like ++ ,--  that is no post/pre increment and decrement.

Suppose we want to take input from the user that must be a positive integer and then print meow. We will do this.
```
while True:
  n = int(input("What is n? "))
  if n > 0:
    break
for i in range(n):
  print("meow")
```
We can do this using functions as well.

```
def main():
  number = get_number()
  meow(number)

def get_number():
  while True:
    n = int(input("What is n? "))
    if n > 0:
      break
    return n
    
def meow(n):
  for i in range(n):
    print("meow")
```

### Python while-else Loop

```
count=0 
while count<5: 
  count+=1 
  print ("Iteration no. ",count)
else: 
  print ("While loop over. Now in else block") 

print ("End of while loop")

Output:
Iteration no. 1
Iteration no. 2
Iteration no. 3
Iteration no. 4
Iteration no. 5
While loop over. Now in else block
End of while loop
```

### Dictionary in Python

We know a List is a set of values but a Dictionary is rather two-dimensional in the sense that it associates something with something else. Just like in a normal dictionary, words are associated with their meanings and written alongside them, here also there are certain keys and values associated with them.
Suppose we want to keep track of who is in which house at Hogwarts. 

| Harry      | Hermione   | Ron        | Draco     |
| ---------- | ---------- | ---------- | --------- |
| Gryffindor | Gryffindor | Gryffindor | Slytherin |
```
// Using Lists
students = ["Harry", "Hermione", "Ron", "Draco"]
houses = ["Gryffindor", "Gryffindor", "Gryffindor", "Slytherin"]

// Using Dictionary
students = {
   "Harry" : "Gryffindor",
   "Hermione" : "Gryffindor",
   "Ron" : "Gryffindor",
   "Draco" : "Slytherin",
} 
print(students["Harry"])
print(students["Hermione"])
print(students["Ron"])
print(students["Draco"])

Output:
Gryffindor
Gryffindor
Gryffindor
Slytherin
// We can write this more dynamically but this will print only the keys

for student in students:
  print(student)

Output:
Harry
Hermione
Ron
Draco
```
What's special about dictionaries is that unlike lists which allow us to use the values using indices like 0, 1, 2 and so on, dictionaries have special indices in the form of keys to get inside them.

```
students = {
   "Harry" : "Gryffindor",
   "Hermione" : "Gryffindor",
   "Ron" : "Gryffindor",
   "Draco" : "Slytherin",
} 
for student in students:
  print(student, students[student])
  
Output:
Harry Gryffindor
Hermione Gryffindor
Ron Gryffindor
Draco Slytherin
```
We can also separate the houses from the respective students.

```
print(student, students[student], sep = ", ")
```

Now, suppose we have more than value associated with our key. Let this be represented as an example.

| S.No | Name     | House      | Patronus             |
| ---- | -------- | ---------- | -------------------- |
| 1.   | Harry    | Gryffindor | Stag                 |
| 2.   | Hermione | Gryffindor | Otter                |
| 3.   | Ron      | Gryffindor | Jack Russell Terrier |
| 4.   | Draco    | Slytherin  |                      |

For this, we will use multiple dictionaries within same students list.

```
students = {
    {"Name" : "Harry", "House" : "Gryffindor", "Patronus" : "Stag"},
    {"Name" : "Hermione", "House" : "Gryffindor", "Patronus" : "Otter"},
    {Name" : "Ron", "House" : "Gryffindor", "Patronus" : "Jack Russell Terrier"},
    {Name" : "Draco", "House" : "Slytherin", "Patronus" : None},
}
for student in students:
  print(student["Name"], student["House"], student["Patronus"], sep =", ")
```

```
def main():
  print_square(3)
  
def print_square(size):

  // For each row in square
  for i in range(size):
  
      // For each brick in row
      for j in range(size):
      
          // Print brick
          print("#", end ="")
          
       print()
main()
```
But we can optimize this program to reduce time and space complexity.

```
def main():
  print_square(3)
  
def print_square(size):
   for i in range(size):
       print("#" * size)
       
Output:
###
###
###
```

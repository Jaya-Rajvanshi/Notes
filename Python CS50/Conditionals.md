Comparing values of two variables. The value may be arithmetic.

```
x = int(input("What is x? "))
y = int(input("What is y? "))
if x<y :
   print("x is less than y")
if x>y :
   print("x is greater than y")
if x=y :
   print("x is equal to y")
```

This looks repetitive and uses way too many if conditions. We can write this using 'elif' keyword.

```
x = int(input("What is x? "))
y = int(input("What is y? "))
if x<y :
   print("x is less than y")
elif x>y :
   print("x is greater than y")
elif x=y :
   print("x is equal to y")
```
The output is still the same but the flow program has changed.

![[Pasted image 20260311231043.png]]

![[Pasted image 20260311231117.png]]
In the second program, if one condition has been checked and found to be True we do not check the rest of the conditions. But there is another keyword 'else' that solves another problem which is if two of the conditions are found to be False we do not really need to check the third. Using else, the flow will look something like this.

![[Pasted image 20260311231612.png]]

There is another keyword 'or'.

```
x = int(input("What is x? "))
y = int(input("What is y? "))
if x < y or x > y :
   print("x is not equal to y")
else :
   print("x is equal to y")
```

```
score = int(input("Score : "))

if score >= 90 and score <= 100 :
    print("Grade : A")
       OR
if 90 <= score <=100 :
    print("Grade : A")
       OR
if score >= 90 :
   print("Grade : A")
elif score >= 80 :
   print("Grade : B")
elif score >= 70 :
   print("Grade : C")
elif score >=60 :
   print("Grade : D")
else  :
   print("Grade : F")
```

```
def is_even(n):
    if n % 2 == 0:
        return True
    else :
        return False

def main():
    x = int(input("What is x? "))
    if is_even(x):
        print("Even")
    else:
        print("Odd")
main()

          OR
def main():
    x = int(input("What is x? "))
    if is_even(x):
        print("Even")
    else:
        print("Odd")
        
def is_even(n):
    if n % 2 == 0:
        return True
    else :
        return False
        
main()
```
Both sequence are correct and will give valid output. Now we can condense our is_even() function.

```
def is_even(n) :
   return True if n % 2 == 0 else False
      OR
   return n % 2 == 0:
```

Using 'match' statements.

```
name = input("What is your name? ")
match name :
   case "Harry" | "Hermione" | "Ron" :
      print("Gryffindor")
   case "Draco" :
      print("Slytherin")
   case _:
      print("Who?")
```
In C language we use 'switch' statements and here in Python we use 'match'. We do not need 'default' case here. We just use an underscore to refer to the general cases.
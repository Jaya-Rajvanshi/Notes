These are a system to store data persistently so that when user comes back to these files, he can run the program again without any problem.

```
names = []

for _ in range(3):
    names.append(input("What is your name? "))
    
for name in sorted(names):
      print(f"Hello, {name}")
```

```
What is your name? Harry
What is your name? Hermione
What is your name? Draco
Hello, Draco
Hello, Harry
Hello, Hermione
```
Now, instead of writing the program and names again and again, we can also save them in a persistent manner. There is a function in Python called as ==open==, whose application is to open a file programmatically so that we, the programmer, can read information from it or write info to it.

```
name = input("What is your name? ")

file = open("names.txt", "w")
file.write(name)
file.close()
```
.write() is a method that comes along with the function open. After running the program, we will see that a file named names.txt has been created with user input name written inside it.

```
python names.py
What is your name? Hermione
>> code names.txt
# This will open the txt file
```
On running the 'python names.py' command again 2 times and giving Harry and Ron as input, we should be able to see all three names inside the txt file. But that is not the case. We see only Ron written there. This is because we are using "w", which will not append these names to the file but rather rewrite the file with the new input again and again. Now, if we replace "w" with "a", which implies append and not replace, we should be able to see all three names.

```
python names.py
What is your name? Hermione
python names.py
What is your name? Harry
```
But on opening the names.txt file, we see that it does have all the names but without any spacing or formatting.
```
RonHermioneHarry
```
Now, we 'rm names.txt', which removes our recently created txt file. We will change our file.write() line.
```
file.write(f"{name}\n")
```
We will see each of the three names written in different lines.
Sometimes, we forget to write the .close() statement and this can cause issues like file getting corrupted or deleted. For this, we have another function called ==with==, that automatically implies what to do to this file and then promptly close it.

```
with open("names.txt", "a") as file:
     file.write(f"{name}\n")
```
Sometimes, we may want to read something from an already created file. For this, the program will look something like this.

```
with open("names.txt", "r") as file:
    lines = file.readlines()

for line in lines:
    print("Hello,", line)
```
readlines() is a function specific to the read-only mode. After running the program through the terminal, the output looks like this.
```
Hello,  Harry

Hello,  Hermione

Hello,  Ron

Hello,  Draco

```
It is not necessarily bad but the formatting and line spacing does look weird. This is due to the fact that print() statement already adds a new line every time it is used but here we are reading lines from a file and this process involves ending any line with a new line character. To solve this, we use end=""  OR  ==rstrip()== function.

```
with open("names.txt", "r") as file:
    lines = file.readlines()

for line in lines:
    print("Hello,", line, end="")

OR

for line in lines:
    print("Hello,", line.rstrip())
```
rstrip() means remove extra characters from the right side (end) of a string. By default, `rstrip()` removes:                                    
- Spaces `" "`
- Tabs `\t`
- Newline `\n`
- `lstrip()` → removes from **left**
- `strip()` → removes from **both sides**

Also, notice that in this program we are doing double work that is we are iterating over the lines and then printing them as well. To reduce this complexity, we can write our program like this.

```
with open("names.txt", "r") as file:
    for line in file:
        print("Hello, ", line.rstrip())
```

```
Hello, Harry
Hello, Hermione
Hello, Ron
Hello, Draco
```
Now, just to brainstorm and get our gears working, suppose we want our output names to be in alphabetical ordering no matter their sequence in the txt file. For this, we will need to take a step back from this latest version of our program. This version reads and prints the content/lines of the file in advance but now we first want to read the lines, sort them and then print them.
Also, when we are opening any file we do not need to define the "r" each time since it is the default mode. 

```
names = []

with open("names.txt") as file:
    for line in file:
        names.append(line.rstrip())

for name in sorted(names):
    print(f"Hello, {name}")
```
Here we are not appending to the file but rather at the end of the list named as 'names'. Simply put, we are first iterating over each line in the file, removing any new line characters after them, putting these lines individually inside the empty list 'names', then sorting the elements inside the list using sorted() function then print out the greeting.
sorted() is a built-in Python function and it takes a list (or any iterable) and returns a **new sorted version** of it. But remember that it does not change the original unsorted list. It can be used with lists, tuples, dictionaries and files. We can go back to our shortened version of the program now that we know the sorted() function.

```
with open("names.txt") as file:
    for line in sorted(file):
        print("Hello,", line.rstrip())
```
Now, suppose we want the contents of our file to be sorted in reverse alphabetical order. For this also, we will use the sorted() function.
```
sorted(iterable, / , *, key=none, reverse=False)
```
This is the complete syntax of the sorted() function. Here, we can simply change the default value of reverse from False to True.

```
names = []

with open("names.txt") as file:
    for line in file:
        names.append(line.rstrip())

for name in sorted(names, reverse=True):
    print(f"Hello, {name}")
```
Now, suppose that we want to store the names of the students as well as their houses. If we simply add the houses next to their names, it will be confusing.

```
Harry
Gryffindor
Hermione
Gryffindor
Ron
Gryffindor
Draco
Slytherin
```
We can save our names.txt file as students.csv where csv stands for Comma Separated Values. We will now keep the relevant houses next to the student names separated by comma.
```
Harry,Gryffindor
Hermione,Gryffindor
Ron,Gryffindor
Draco,Slytherin
```
There is function called as split() used to split string into two or more multiple pieces based on the parameter specified. We will use this inside our students.py file. Ultimately, split() is going to return us a list with all the pieces of text that were split as members of the list individually. While using this function, it is common to consider each line inside the file as row and all the split pieces of string as columns.

```
with open("students.csv") as file:
    for line in file:
        row = line.rstrip().split(",")
        print(f"{row[0]} is in {row[1]}")
```

```
Harry is in Gryffindor
Hermione is in Gryffindor
Ron is in Gryffindor
Draco is in Slytherin
```
We can assign two variables at once in Python. For example, here we want a separate variable for student names and their houses. This makes our code a little more readable.
```
with open("students.csv") as file:
    for line in file:
        name, house = line.rstrip().split(",")
        print(f"{name} is in {house}")
```
This is not sorted and also we now want to use a dictionary to implement this.

```
students = []

with open("students.csv") as file:
    for line in file:
         name, house = line.rstrip().split(",")
         student = {"name": name, "house": house}
         students.append(student)

def get_name(student):
    return student["name"]
for student in sorted(students, key=get_name):
    print(f"{student['name']} is in {student['house']}")
```
Now we get our names in a sorted manner. We can reverse this as well using reverse parameter inside the sorted function.

```
Draco is in Slytherin
Harry is in Gryffindor
Hermione is in Gryffindor
Ron is in Gryffindor
```
Suppose we do not want to create another function like get_name and instead sort on the basis of student names and define this condition inside sorted() function only. For this, program will change a little bit.

```
students = []

with open("students.csv") as file:
    for line in file:
         name, house = line.rstrip().split(",")
         student = {"name": name, "house": house}
         students.append(student)

for student in sorted(students, key=lambda student: student["name"]):
    print(f"{student['name']} is in {student['house']}")
```
In this way we have reduced our complexity required to define another function and then calling it. After appending dictionary to our list named as students, it will look like this.

```
[
  {"name": "Harry", "house": "Gryffindor"},
  {"name": "Hermione", "house": "Gryffindor"},
  {"name": "Draco", "house": "Slytherin"}
]
```
The 'key' parameter tells Python how to sort and lambda is a short function that for each student, uses their **name** for sorting.
If we change our students.csv file to look something like this and then run the above program, the output will surprise us.

```
Harry,Number Four,Privet Drive
Ron,The Burrow
Draco,Malfoy Manor
```

```
ValueError : too many values to unpack (expected 2)
```
This implies that for Harry, we have provided more values than required while the dictionary expected only 2, that is, a student name and their respective house.

```
import csv

students = []

with open("students.csv") as file:
    reader = csv.reader(file)
    for name, home in reader:
        students.append({"name" : name, "home" : home})

for student in sorted(students, key=lambda student: student["name"]):
    print(f"{student['name']} is from {student['home']}")
```
Here, csv.reader() reads the file row by row. Each row becomes a list. For example

```
Harry, "Number Four, Privet Drive"   //becomes
["Harry", "Number Four, Privet Drive"]
```
for name, home in reader tries to unpack each row into name and home.

```
students.append({"name" : name, "home" : home}) //creates a dictionary
{"name": "Harry", "home": "Number Four, Privet Drive"}
```
Now, we will write another program inside 'students2.py' that will append names and respective home addresses to the csv file.

```
import csv

name = input("What is your name? ")
home = input("Where is your home? ")

with open("students2.csv", "a") as file:
    writer = csv.writer(file)
    writer.writerow([name, home])
```
We will see that on giving input the csv file will be automatically created and appended.

```
What is your name? Harry
Where is your home? Number Four, Privet Drive
```

```
>>students2.csv
Harry, "Number Four, Privet Drive"
```
There is another way of printing these names and home addresses. We can use dictionary for this and a function called as DictWriter(). This function helps us write data in the form of dictionary. 'fieldnames' define column names 'name' and 'home'. The writer.writerow() function writes one row into the csv file.

```
import csv

name = input("What is your name? ")
home = input("Where is your home? ")

with open("students2.csv", "a") as file:
    writer = csv.DictWriter(file, fieldnames=["name", "home"])
    writer.writerow({"name" : name, "home" : home})
```
Now, there is another library called PIL (pillow) which is useful in handling image files and generating them. Using File I/O, we can manipulate not only text files but also imagery files.
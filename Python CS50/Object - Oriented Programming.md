So far we have been writing programs that are procedural, that is, we implemented procedures and functions. Object Oriented Programming is a way of writing code where we organize everything into - Objects (things) and Classes (blueprint of things).

```
def main():
    student = get_student()
    print(f"{student[0]} from {student[1]}")
    
def get_student():
    name = input("Name: ")
    house = input("House: ")
    return (name,house)
    
if __name__ == "__main__":
    main()
```
student variable stores the value returned from get_student(). Here student is a tuple which is used to print the details of student input by the user. The get_student() function returns a tuple since return values are inside parenthesis. And if condition is in case we are running the original file and not importing it inside another file.
Tuples are generally used in cases where there is no requirement of any changes or modifications present inside the data type. That is, not even the programmer has to change the contents of the tuple. Since tuples are immutable.
Now suppose we have a character called Padma in Harry Potter franchise and in the movies she is shown to be of Gryffindor house but in the books she is from Ravenclaw. We can create a conditional case for this situation.

```
def main():
    student = get_student()
    if student[0] == "Padma":
        student[1] == "Ravenclaw"
    print(f"{student[0]} from {student[1]}")
    
def get_student():
    name = input("Name: ")
    house = input("House: ")
    return (name,house)
    
if __name__ == "__main__":
    main()
```
But on running the program, we get an Exception called as TypeError. As we said before, tuples are immutable so we cannot change location 0 to something else. For this, we can simply change the data type from tuple to list.

```
Name: Padma
House: Gryffindor

TypeError: 'tuple' object does not support item assignment
```

```
def main():
    student = get_student()
    if student[0] == "Padma":
        student[1] == "Ravenclaw"
    print(f"{student[0]} from {student[1]}")
    
def get_student():
    name = input("Name: ")
    house = input("House: ")
    return [name,house]
    
if __name__ == "__main__":
    main()
```
Now we talk about 'Classes' in Python. They allow us to create our own data types and give them a name. We will use this Class to define our own data type and not use tuples or lists.

```
class Student:
     ...

def main():
    student = get_student()
    print(f"{student.name} from {student.house}")
    
def get_student():
    student = Student()
    student.name = input("Name: ")
    student.house = input("House: ")
    return student
    
if __name__ == "__main__":
    main()
```
Also Objects are mutable by default but we as programmers can make them immutable as well. So we can get best of both worlds.
Here in the above program, inside the main() function, student is an Object of the class Student and it stores the result returned by the function get_student() after calling it. And get_student() is a function to create and return a student object. student = Student() creates a new Student object. student.name is an attribute that takes input provided by the user and stores it in object. Similar case for student.house.
There are also 'methods' related to Classes, in which we can define certain functions and they behave in a special way.
We can define a standard function inside the Class created in the previous program. 
__ init __ is a Dunder method and called an instance method, defined by the authors of Python and if we want to initialize the contents of an object from a class, we have to define this method.

```
class Student:
    def __init__(self):
            

def main():
    student = get_student()
    print(f"{student.name} from {student.house}")
    
def get_student():
    student = Student()
    student.name = input("Name: ")
    student.house = input("House: ")
    return student
    
if __name__ == "__main__":
    main()
```
We, the programmers can raise exceptions ourselves using a keyword called 'raise'.

```
class Student:
    def __init__(self, name, house):
        if not name:
            raise ValueError
        self.name = name
        self.house = house
            
def main():
    student = get_student()
    print(f"{student.name} from {student.house}")
    
def get_student():
    name = input("Name: ")
    house = input("House: ")
       return Student(name, house)
        
if __name__ == "__main__":
    main()
```
The Student class defines a Student blueprint. __ init __ is a special function/constructor. It runs automatically when we create an object. 

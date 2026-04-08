Unit Testing means testing small parts of our code to check whether they work correctly. We have created a program called as calculator.py which simply gives the square of a number. Now, we create another program named test_calculator.py and import square function into it.

```
from calculator import square

def main():
    test_square()

def test_square():
    if square(2) != 4:
       print("2 squared was not 4")
    if sqaure(3) != 9:
       print("3 squared was not 9")

if __name__ == "__main__":
    main()
```
On running the test_calculator.py on CLI, nothing is printed since we have not given any print statement in case everything is working fine. Now, if we introduce some bug in our calculator.py file, this will happen.

```
def main():
    x = int(input("What is x? "))
    print("x squared is ", square(x))

def square(n):
    return n + n

if __name__ == "__main__":
    main()
```

```
python test_calculator.py 
3 squared was not 9
```
Here, we have failed one of the test cases since 2+2 is also 4. So we have managed to perform basic Unit Testing. There can be another approach to this so that we can check all test cases without there being any anomalies.
There is a keyword 'assert' in Python. Using this we do not need to use if conditions to check whether the square of the value is correct or not. This keyword asserts that given statement written after it is always True and we do not need to write any boolean expression for this.

```
from calculator import square

def main():
    test_square()

def test_square():
    assert square(2) == 4:
    assert sqaure(3) == 9:

if __name__ == "__main__":
    main()
```
But there is still a possibility of AssertionError. It happens when we expected something to be definitely True but it turned out be False. To catch this, we use try and catch keywords.

```
from calculator import square

def main():
    test_square()

def test_square():
    try:
        assert square(2) == 4
    except Assertionerror:
        print("2 squared was not 4")
    try:
        assert sqaure(3) == 9
    except AssertionError:
        print("3 squared was not 9")

if __name__ == "__main__":
    main()
```
We can add more test cases to this like -2, -3, 0.
Now, there is a third-party library called ==pytest== that is useful in testing our programs and we do not need to write so many lines of code manually. This is implemented in test_calculator2.py

```
from calculator import square

def test_square():
    assert square(2) == 4
    assert square(3) == 9
    assert square(-2) == 4
    assert square(-3) == 9
    assert square(0) == 0
```

```
pytest test_calculator2.py
```
After writing this command in the terminal it will display all test cases have been passed.
Now, there is a problem with this improvised version of program. In case there is test that does not pass, system does not check rest of the test cases at all. This is problematic since any programmer would want to know exactly which test cases are failing and not just one.
Let us divide our test_square() function into separate categories.

```
from calculator import square

def test_positive():
    assert square(2) == 4
    assert square(3) == 9
    
def test_negative():
    assert square(-2) == 4
    assert square(-3) == 9
    
def test_zero():
    assert square(0) == 0
```
Now, even if one of the test categories fail, others will still be checked. Suppose someone inputs a string instead of an integer value, then we need to raise an exception and catch it. For this inside the pytest library, we have a function called ==pytest.raises()==. 

```
import pytest
from calculator import square

def test_positive():
    assert square(2) == 4
    assert square(3) == 9
    
def test_negative():
    assert square(-2) == 4
    assert square(-3) == 9
    
def test_zero():
    assert square(0) == 0

def test_str():
    with pytest.raises(TypeError):
         square("cat")
```

This is another program called hello.py.
```
def main():
    name = input("What is your name? ")
    hello(name)

def hello(to = "world"):            
    print("Hello, ", to)

if __name__ == "__main__":
    main()
```
If we create another file for testing this program, test_hello.py and import the hello function into this file, we face a situation.
```
from hello import hello

def test_hello():
    hello("David") = "hello, David"
```
Here, the function does not return any value and that is essential while writing any program. So now we change our hello.py program and hello function inside it to return something.

```
def main():
    name = input("What is your name? ")
    print(hello(name))

def hello(to = "world"):            
    return f"Hello, {to}"

if __name__ == "__main__":
    main()
```
We can write our test_hello.py like this also.

```
from hello import hello

def test_hello():
    assert hello("David") == "Hello, David"
    assert hello() == "Hello, world"
```
Or we can categorize the test_hello() function.
```
from hello import hello

def test_default():
    assert hello() == "Hello, world"
    
def test_argument():
    assert hello("David") == "Hello, David" 
```
We can use assert keyword inside loops as well.

```
from hello import hello

def test_default():
    assert hello() == "Hello, world"
    
def test_argument():
    for name in ["Hermione", "Harry", "Ron"]:
        assert hello(name) == f"Hello, {name}" 
```


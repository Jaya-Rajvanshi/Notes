Regular expressions are patterns used to match text. Think of them as **search rules** for strings. Suppose we search in Google for "Emily". Regex is like a smart search. It finds all words starting from E, all phone numbers, email addresses relevant to the name Emily. Python uses "import re" to implement regular expressions.
Assume we want to validate a user's email address and we have to write a program for it.
Program name is validate.py

```
email = input("What is your email? ").strip()

if "@" in email:
    print("Valid")
else:
    print("Invalid")
```
But this is a buggy program since it automatically validates the email even if the email is a single '@' sign. To make this more effective, we can rewrite our program.

```
email = input("What is your email? ").strip()

if "@" in email and "." in email:
    print("Valid")
else:
    print("Invalid")
```
But still the same issue persists. If user gives '@.' as input it will still be considered a valid email.
```
email = input("What is your email? ").strip()

username, domain = email.split("@")
if (username) and ("." in domain):
    print("Valid")
else:
    print("Invalid")
```
Or we can write this like

```
email = input("What is your email? ").strip()

username, domain = email.split("@")
if (username) and (domain.endswith("edu")):
    print("Valid")
else:
    print("Invalid")
```
But on giving an input like 'malan@.edu' it will considered valid. Let us first write this same program implementation using the 're' library. This is no better than our previous program but we are at least using a relevant library and re.search() function.

```
import re 

email = input("What is your email? ").strip()

if re.search("@", email): 
    print("Valid")
else:
    print("Invalid")
```
The function re.search() has a broader syntax.
re.search(pattern, string, flags=0). It can take a whole lot of special symbols and some of them are -

| Symbol | Description                                                                       |
| ------ | --------------------------------------------------------------------------------- |
| .      | any character except the newline                                                  |
| *      | 0 or more repetitions                                                             |
| +      | 1 or more repetitions                                                             |
| ?      | 0 or 1 repetitions                                                                |
| {m}    | m repetitions                                                                     |
| {m, n} | m-n repetitions                                                                   |
| ^      | matches the start of the string                                                   |
| $      | matches the end of the string or just before the newline at the end of the string |
| [ ]    | set of characters                                                                 |
| [ ^ ]  | complementing the set                                                             |
Now, if we define a pattern inside the re.search() function, we may have better implementation.

```
import re 

email = input("What is your email? ").strip()

if re.search(".*@.*", email): 
    print("Valid")
else:
    print("Invalid")
```
The pattern defined implies that there should be something before @ and after it except newline. But on providing input like malan@, it still comes out to be valid. This is because we are using the symbol star/asterisk which allows for 0 repetitions so even if there is nothing after @, it is still valid. Let us instead use + symbol which demands at least one repetition.
```
import re 

email = input("What is your email? ").strip()

if re.search(".+@.+", email):    // can also write ..*@.*
    print("Valid")               // This would mean at least a single char
else:                            // should be there
    print("Invalid")
```

```
import re 

email = input("What is your email? ").strip()

if re.search(r"..+@.+\.edu", email): 
    print("Valid")
else:
    print("Invalid")
```
Here, \ separates the dot which is a special symbol indicating characters except newline and the dot that should differentiate between the username and domain name. Also, we do not want Python to interpret this back slash as newline (\n) so we use 'r' here which indicates raw string, to be interpreted exactly like it is written.

```
python validate.py
What is your email? malan@harvard?edu
Invalid
What is your email? malan@@@harvard.edu
Valid
```
So, as we can observe there is still some issues and bugs with this program. Let us add two more special symbols- ^ and $. This tells Python to look for the exact same string pattern and nothing differentiating.

```
import re 

email = input("What is your email? ").strip()

if re.search(r"^..+@.+\.edu$", email): 
    print("Valid")
else:
    print("Invalid")
```

```
What is your email? malan@harvard.edu.
Invalid                            // It works
```
Now, to fix our issue with 'malan@@harvard.edu', we use some other special symbols. 
[ ^@] implies that any character except @ then + means one more character after it. Then after checking for @ we again have [ ^@ ] which means any character except @ again.

```
import re 

email = input("What is your email? ").strip()

if re.search(r"^[^@]+@[^@]+\.edu$", email): 
    print("Valid")
else:
    print("Invalid")
```

```
What is your email? malan@@@harvard.edu
Invalid
What is your email? .edu@.edu
Invalid
What is your email? .edu@something.edu
Valid
```
To make our program more restrictive and specific, we can define a set of characters permissible as usernames and as domain names.

```
import re 

email = input("What is your email? ").strip()

if re.search(r"^[a-zA-Z0-9]+@[a-zA-Z0-9]+\.edu$", email): 
    print("Valid")
else:
    print("Invalid")
```

```
What is your name? .edu@malan.edu
Invalid
What is your name? .edu@malan@harvard.edu
Invalid
```
But we do not need to write all the characters we need every time we write our program. For this we have '\w' which implies word that is any character or alpha numeric symbol or underscore as well.

```
import re 

email = input("What is your email? ").strip()

if re.search(r"^\w+@\w+\.edu$", email): 
    print("Valid")
else:
    print("Invalid")
```
Some more special symbols - 

| Symbol    | Description                                      |
| --------- | ------------------------------------------------ |
| \d        | decimal digit                                    |
| \D        | Not a decimal digit                              |
| \s        | whitespace characters                            |
| \S        | Not a whitespace characters                      |
| \w        | word character as well as numbers and underscore |
| \W        | Not a word character                             |
| A\|B      | either A or B                                    |
| ( ... )   | A group                                          |
| ( ?:... ) | Non capturing version                            |
In case we want to give user options for domain names, we can make changes to our program.

```
import re 

email = input("What is your email? ").strip()

if re.search(r"^\w+@\w+\.(com|gov|net|org|edu)$", email): 
    print("Valid")
else:
    print("Invalid")
```

There are various functions with 're' library, like re.IGNORECASE, re.MULTILINE, re.DOTALL.
Ignorecase is for ignoring constraints of lower or upper case, that is, user may write in any case and it will still be relevant. Multiline is for input spanning more than one line. Using Dotall we can configure the system to recognize not just any character except new line but also any character including new line.

```
import re 

email = input("What is your email? ").strip()

if re.search(r"^\w+@\w+\.(com|gov|net|org|edu)$", email, re.IGNORECASE): 
    print("Valid")
else:
    print("Invalid")
```

```
What is your email? MALAN@HARVARD.EDU
Valid
```
When people input their names, sometimes they may have different approaches to writing their names. Like in the US, people first write their last names then first names separated by a comma. For a simple Python program, this may create issues.

```
name = input("What is your name? ").strip()
print(f"Hello, {name}")
```

```
What is your name? Malan, David
Hello, Malan, David
```
This looks weird.

```
name = input("What is your name? ").strip()

if (", ") in name:
    last, first = name.split(", ")
    name = f"{first} {last}"       //To override user's input style
print(f"Hello, {name}")
```

```
What is your name? Malan, David
Hello, David Malan
```
Suppose someone forgets to provide space after the comma, then ValueError is displayed. This implies that our code is fragile and does not handle exceptions. 
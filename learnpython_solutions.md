Here's my solutions to www.learnpython.org challenges

## Learn the Basics

[**1. Hello, World!**](https://learnpython.org/en/Hello%2C_World%21)

```python
print("Hello, World!")
```

[**2. Variables and Types**](https://learnpython.org/en/Variables_and_Types)

```python
mystring = "hello"
myfloat = 10.0
myint = 20

if mystring == "hello":
    print("String: %s" % mystring)
if isinstance(myfloat, float) and myfloat == 10.0:
    print("Float: %f" % myfloat)
if isinstance(myint, int) and myint == 20:
    print("Integer: %d" % myint)
```

[**3. Lists**](https://learnpython.org/en/Lists)

```python
numbers = []
strings = []
names = ["John", "Eric", "Jessica"]

# write your code here
second_name = names[1]

numbers.append(1)
numbers.append(2)
numbers.append(3)

strings.append("hello")
strings.append("world")

# this code should write out the filled arrays and the second name in the names list (Eric).
print(numbers)
print(strings)
print("The second name on the names list is %s" % second_name)
```

[**4. Basic Operators**](https://learnpython.org/en/Basic_Operators)

```python
x = object()
y = object()

# TODO: change this code
x_list = [x] * 10
y_list = [y] * 10
big_list = x_list + y_list

print("x_list contains %d objects" % len(x_list))
print("y_list contains %d objects" % len(y_list))
print("big_list contains %d objects" % len(big_list))

# testing code
if x_list.count(x) == 10 and y_list.count(y) == 10:
    print("Almost there...")
if big_list.count(x) == 10 and big_list.count(y) == 10:
    print("Great!")
```

[**5. String Formatting**](https://learnpython.org/en/String_Formatting)

```python
#%s - String (or any object with a string representation, like numbers)
#%d - Integers
#%f - Floating point numbers
#%.<number of digits>f - Floating point numbers with a fixed amount of digits to the right of the dot.
#%x/%X - Integers in hex representation (lowercase/uppercase)

data = ("John", "Doe", 53.44)
format_string = "Hello %s %s. Your current balance is $%s."

print(format_string % data)
```

[**6. Basic String Operations**](https://learnpython.org/en/Basic_String_Operations)

```python
s = "Strings are awesome!"
# Length should be 20
print("Length of s = %d" % len(s))

# First occurrence of "a" should be at index 8
print("The first occurrence of the letter a = %d" % s.index("a"))

# Number of a's should be 2
print("a occurs %d times" % s.count("a"))

# Slicing the string into bits
print("The first five characters are '%s'" % s[:5]) # Start to 5
print("The next five characters are '%s'" % s[5:10]) # 5 to 10
print("The thirteenth character is '%s'" % s[12]) # Just number 12
print("The characters with odd index are '%s'" %s[1::2]) #(0-based indexing)
print("The last five characters are '%s'" % s[-5:]) # 5th-from-last to end

# Convert everything to uppercase
print("String in uppercase: %s" % s.upper())

# Convert everything to lowercase
print("String in lowercase: %s" % s.lower())

# Check how a string starts
if s.startswith("Str"):
    print("String starts with 'Str'. Good!")

# Check how a string ends
if s.endswith("ome!"):
    print("String ends with 'ome!'. Good!")

# Split the string into three separate strings,
# each containing only a word
print("Split the words of the string: %s" % s.split(" "))

```

[**7. Conditions**](https://learnpython.org/en/Conditions)

```python
# change this code
number = 16
second_number = 0
first_array = [1, 15, 2]
second_array = [1,2]

if number > 15:
    print("1")

if first_array:
    print("2")

if len(second_array) == 2:
    print("3")

if len(first_array) + len(second_array) == 5:
    print("4")

if first_array and first_array[0] == 1:
    print("5")

if not second_number:
    print("6")
```

[**8. Loops**](https://learnpython.org/en/Loops)

```python
numbers = [
    951, 402, 984, 651, 360, 69, 408, 319, 601, 485, 980, 507, 725, 547, 544,
    615, 83, 165, 141, 501, 263, 617, 865, 575, 219, 390, 984, 592, 236, 105, 942, 941,
    386, 462, 47, 418, 907, 344, 236, 375, 823, 566, 597, 978, 328, 615, 953, 345,
    399, 162, 758, 219, 918, 237, 412, 566, 826, 248, 866, 950, 626, 949, 687, 217,
    815, 67, 104, 58, 512, 24, 892, 894, 767, 553, 81, 379, 843, 831, 445, 742, 717,
    958, 609, 842, 451, 688, 753, 854, 685, 93, 857, 440, 380, 126, 721, 328, 753, 470,
    743, 527
]

# your code goes here
for number in numbers:
    if (number == 237):
        break
    if (number % 2 == 0):
        print(number)
```

[**9. Functions**](https://learnpython.org/en/Functions)

```python
# Modify this function to return a list of strings as defined above
def list_benefits():
    return ["More organized code", "More readable code", "Easier code reuse", "Allowing programmers to share and connect code together"]

# Modify this function to concatenate to each benefit - " is a benefit of functions!"
def build_sentence(benefit):
    return benefit + " is a benefit of functions!"

def name_the_benefits_of_functions():
    list_of_benefits = list_benefits()
    for benefit in list_of_benefits:
        print(build_sentence(benefit))

name_the_benefits_of_functions()
```

[**10. Classes and Objects**](https://learnpython.org/en/Classes_and_Objects)

```python
# define the Vehicle class
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str
# your code goes here
car1 = Vehicle()
car2 = Vehicle()

car1.name = "Fer"
car1.kind = "convertible"
car1.color = "red"
car1.value = 60000.00

car2.name = "Jump"
car2.kind = "van"
car2.color = "blue"
car2.value = 10000.00
# test code
print(car1.description())
print(car2.description())
```

[**11. Dictionaries**](https://learnpython.org/en/Dictionaries)

```python
phonebook = {
    "John" : 938477566,
    "Jack" : 938377264,
    "Jill" : 947662781
}

# write your code here
phonebook["Jake"] = 938273443

del phonebook["Jill"]
# testing code
if "Jake" in phonebook:
    print("Jake is listed in the phonebook.")
if "Jill" not in phonebook:
    print("Jill is not listed in the phonebook.")
```

[**12. Modules and Packages**](https://learnpython.org/en/Modules_and_Packages)

```python
import re

# Your code goes here
match_functions = []
substr = "find"
for functionName in dir(re):
    if substr in functionName:
        match_functions.append(functionName)

print(sorted(match_functions))
```


## Data Science Tutorials

[**1. Numpy Arrays**](https://learnpython.org/en/Numpy_Arrays)

```python
weight_kg = [81.65, 97.52, 95.25, 92.98, 86.18, 88.45]

import numpy as np

# Create a numpy array np_weight_kg from weight_kg
np_weight_kg = np.array(weight_kg)
# Create np_weight_lbs from np_weight_kg
np_weight_lbs = np_weight_kg * 2.2
# Print out np_weight_lbs
print(np_weight_lbs)
# [ 179.63   214.544  209.55   204.556  189.596  194.59 ]
```

[**2. Pandas Basics**](https://learnpython.org/en/Pandas_Basics)
>No real exercices here, just some tests.

```python
dict = {"country": ["Brazil", "Russia", "India", "China", "South Africa"],
       "capital": ["Brasilia", "Moscow", "New Dehli", "Beijing", "Pretoria"],
       "area": [8.516, 17.10, 3.286, 9.597, 1.221],
       "population": [200.4, 143.5, 1252, 1357, 52.98] }

import pandas as pd
brics = pd.DataFrame(dict)
print(brics)
#      area    capital       country  population
# 0   8.516   Brasilia        Brazil      200.40
# 1  17.100     Moscow        Russia      143.50
# 2   3.286  New Dehli         India     1252.00
# 3   9.597    Beijing         China     1357.00
# 4   1.221   Pretoria  South Africa       52.98
# Set the index for brics
brics.index = ["BR", "RU", "IN", "CH", "SA"]

# Print out brics with new index values
print(brics)
#      area    capital       country  population
#BR   8.516   Brasilia        Brazil      200.40
#RU  17.100     Moscow        Russia      143.50
#IN   3.286  New Dehli         India     1252.00
#CH   9.597    Beijing         China     1357.00
#SA   1.221   Pretoria  South Africa       52.98
# Import the cars.csv data: cars
cars = pd.read_csv('cars.csv')

# Print out cars
print(cars)
#     Unnamed: 0  cars_per_cap        country drives_right
#   0         US           809  United States         True
#   1        AUS           731      Australia        False
#   2        JAP           588          Japan        False
#   3         IN            18          India        False
#   4         RU           200         Russia         True
#   5        MOR            70        Morocco         True
#   6         EG            45          Egypt         True
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out country column as Pandas Series
print(cars['cars_per_cap'])
#    US     809
#    AUS    731
#    JAP    588
#    IN      18
#    RU     200
#    MOR     70
#    EG      45

# Print out country column as Pandas DataFrame
print(cars[['cars_per_cap']])
#    Name: cars_per_cap, dtype: int64
#         cars_per_cap
#    US            809
#    AUS           731
#    JAP           588
#    IN             18
#    RU            200
#    MOR            70
#    EG             45

# Print out DataFrame with country and drives_right columns
print(cars[['cars_per_cap', 'country']])
#         cars_per_cap        country
#    US            809  United States
#    AUS           731      Australia
#    JAP           588          Japan
#    IN             18          India
#    RU            200         Russia
#    MOR            70        Morocco
#    EG             45          Egypt

# Print out first 4 observations
print(cars[0:4])
#     cars_per_cap        country drives_right
#US            809  United States         True
#AUS           731      Australia        False
#JAP           588          Japan        False
#IN             18          India        False

# Print out fifth, sixth, and seventh observation
print(cars[4:6])
#     cars_per_cap  country drives_right
#RU            200   Russia         True
#MOR            70  Morocco         True
```

`loc` is label-based, which means that you have to specify rows and columns based on their row and column labels. `iloc` is integer index based, so you have to specify rows and columns by their integer index like you did in the previous exercise.

```python
# Print out observation for Japan
print(cars.iloc[2])
#  cars_per_cap      588
#  country         Japan
#  drives_right    False
#  Name: JAP, dtype: object

# Print out observations for Australia and Egypt
print(cars.loc[['AUS', 'EG']])
#       cars_per_cap    country drives_right
#  AUS           731  Australia        False
#  EG             45      Egypt         True
```

## Advanced Tutorials

[**1. Generators**](https://learnpython.org/en/Generators)

```python
# fill in this function
def fib():
  a, b = 1, 1
  while True:
    a, b = b, a + b
    yield a
  

# testing code
import types
if type(fib()) == types.GeneratorType:
    print("Good, The fib function is a generator.")

    counter = 0
    for n in fib():
        print(n)
        counter += 1
        if counter == 10:
            break
```

[**2. List Comprehensions**](https://learnpython.org/en/List_Comprehensions)

```python
numbers = [34.6, -203.4, 44.9, 68.3, -12.2, 44.6, 12.7]
newlist = [nb for nb in numbers if nb > 0]
print(newlist) 
# [34.6, 44.9, 68.3, 44.6, 12.7]
```

[**3. Multiple Function Arguments**](https://learnpython.org/en/Multiple_Function_Arguments)

```python
def foo(first, second, third, *therest):
    print("First: %s" % first)
    print("Second: %s" % second)
    print("Third: %s" % third)
    print("And all the rest... %s" % list(therest))

foo(1, 2, 3, 4, 5, 6)
# First: 1
# Second: 2
# Third: 3
# And all the rest... [4, 5, 6]

def bar(first, second, third, **options):
    if options.get("action") == "sum":
        print("The sum is: %d" %(first + second + third))

    if options.get("number") == "first":
        return first

result = bar(1, 2, 3, action = "sum", number = "first")
print("Result: %d" %(result))
# The sum is: 6
# Result: 1
# edit the functions prototype and implementation
def foo(a, b, c, *extraArgs):
    return len(extraArgs)

def bar(a, b, c, **options):
    return options.get("magicnumber") == 7


# test code
if foo(1,2,3,4) == 1:
    print("Good.")
if foo(1,2,3,4,5) == 2:
    print("Better.")
if bar(1,2,3,magicnumber = 6) == False:
    print("Great.")
if bar(1,2,3,magicnumber = 7) == True:
    print("Awesome!")
```

[**4. Regular Expressions**](https://learnpython.org/en/Regular_Expressions)

```python
# Exercise: make a regular expression that will match an email
import re
def test_email(your_pattern):
    pattern = re.compile(your_pattern)
    emails = ["john@example.com", "python-list@python.org", "wha.t.`1an?ug{}ly@email.com"]
    for email in emails:
        if not re.match(pattern, email):
            print("You failed to match %s" % (email))
        elif not your_pattern:
            print("Forgot to enter a pattern!")
        else:
            print("Pass")
# Your pattern here!
pattern = r"\"?([-a-zA-Z0-9.`?{}]+@\w+\.\w+)\"?"
test_email(pattern)
```

[**5. Exception Handling**](https://learnpython.org/en/Exception_Handling)

```python
print(a) # NameError: name 'a' is not defined
try:
    print(a)
except NameError:
    print('Fail')
# Fail
# Handle all the exceptions!
#Setup
actor = {"name": "John Cleese", "rank": "awesome"}

#Function to modify, should return the last name of the actor - think back to previous lessons for how to get it
def get_last_name():
    try:
        return actor["last_name"]
    except KeyError:
        try:
            actor_identity = actor["name"].split()
            lastname = actor_identity[1]
            return lastname
        except Exception as e:
            return 'Fail'

#Test code
get_last_name()
print("All exceptions caught! Good job!")
print("The actor's last name is %s" % get_last_name())

# All exceptions caught! Good job!
# The actor's last name is Cleese
```

[**6. Sets**](https://learnpython.org/en/Sets)

```python
a = set(["Jake", "John", "Eric"])
print(a) # {'Eric', 'John', 'Jake'}
b = set(["John", "Jill"])
print(b) # {'John', 'Jill'}

print(a.intersection(b)) # {'John'}
print(b.intersection(a)) # {'John'}

print(a.difference(b)) # {'Eric', 'Jake'}
print(b.difference(a)) # {'Jill'}

print(a.symmetric_difference(b)) # {'Eric', 'Jake', 'Jill'}
print(b.symmetric_difference(a)) # {'Eric', 'Jake', 'Jill'}

print(a.union(b)) # {'Eric', 'John', 'Jake', 'Jill'}
print(b.union(a)) # {'Eric', 'John', 'Jake', 'Jill'}
```

[**7. Serialization**](https://learnpython.org/en/Serialization)

```python
import json

# fix this function, so it adds the given name
# and salary pair to salaries_json, and return it
def add_employee(salaries_json, name, salary):
    salaries = json.loads(salaries_json)
    salaries[name] = salary

    return json.dumps(salaries)

# test code
salaries = '{"Alfred" : 300, "Jane" : 400 }'
new_salaries = add_employee(salaries, "Me", 800)
decoded_salaries = json.loads(new_salaries)
print(decoded_salaries["Alfred"]) # 300
print(decoded_salaries["Jane"]) # 400
print(decoded_salaries["Me"]) # 800
```

[**8. Partial functions**](https://learnpython.org/en/Partial_functions)

```python
# So easy, JS help me check nodeschool.io
#Following is the exercise, function provided:
from functools import partial
def func(u,v,w,x):
    return u*4 + v*3 + w*2 + x
#Enter your code here to create and print with your partial function
four = partial(func, 5)
three = partial(four, 10)
dbl = partial(three, 5)
add = partial(dbl, 0)

print(add()) # 60
```

[**9. Code Introspection**](https://learnpython.org/en/Code_Introspection)

```python
#Code introspection is the ability to examine classes, functions and keywords to know what they are, what they do and what they know.
#Python provides several functions and utilities for code introspection.

# help()
# dir() 
# hasattr() 
# id() 
# type() 
# repr() 
# callable() 
# issubclass() 
# isinstance() 
# __doc__ 
# __name__
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

# Print a list of all attributes of the Vehicle class.
# Your code goes here
print(dir(Vehicle()))
# ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'color', 'description', 'kind', 'name', 'value']
```

[**10. Closures**](https://learnpython.org/en/Closures)

```python
# your code goes here
def multiplier_of(nb):
    def multiplier_by(n):
        return nb * n
    return multiplier_by
     
multiplywith5 = multiplier_of(5)
print(multiplywith5(9))
```

[**11. Decorators**](https://learnpython.org/en/Decorators)

```python

```

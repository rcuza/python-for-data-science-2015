# Objectives
Students will be able to
- write Python programs that use if-elses, for loops, lists, dictionaries
- read the documentation for external libraries and use those libraries
- use the basic functionality of `pandas` for data analysis
- use iPython notebook to conduct their data analysis

# Prerequisites
- strongly recommend Learn Python the Hard Way
- basic Python

# Agenda
0. Set up programming environment
1. Warm Up
2. Review of Basic Python
3. Using Other Libraries
4. Intro to Pandas
5. Intro to Sci-kit Learn (time permitting)
6. Closing thoughts

# Set Up Programming Environment (10)
## Download and Installation
Go through these steps on your own computer, but do so in collaboration with your neighbor.

0. Download and install anaconda (before class) [here](http://continuum.io/downloads).
1. Open Terminal
2. Run this command to create our development environment: `conda create -n pds pandas matplotlib ipython ipython-notebook scikit-learn` (This may take a few minutes)
3. Run this command to activate that environment: `source activate pds`
4. Run this command to open iPython notebook: `ipython notebook`

### Exercise: Getting Familiar with iPython Notebook
Run the following code in iPython notebook by typing it into a cell and pressing either the Play button or Shift+Enter to execute.

```python
print "Hello"
```

# Review of Basic Python (20)
## The Basic Data Types
What are the basic data types?
- Integers, e.g. 1, 2, 3
- Floating point numbers, e.g 2.3, 3.7
- String, e.g. "John Krasinski"
- bool, True or False
- None, which just corresponds to empty or null, if you've used other languages

## Variables
Now let's talk variables. What's a variable? It's a placeholder for a value.
```python
>>> x = 5
>>> y = 2
>>> x + y
7
>>> x = 3
>>> x + y
5
```

Note: there are rules for valid variable names, e.g. no spaces, no hyphens.

### Exercise
Do this exercise solo.

Set a variable called `age` equal to your age. Then create a new variable called `future_age` that you set equal to `age` + 10. Then print `age` and separately print `future_age`.

## Lists (30)
Lists is a super useful data type.
It's an ordered collection of items, which you can modify by adding or removing elements.

Let's learn the syntax of a list:
```python
>>> x = [1, 2, 3, 4, 5]
>>> len(x)
5
>>> # what's between the brackets is called the index
>>> x[0]
1
>>> x[1]
2
>>> x[4]
5
>>> x[6]
IndexError
>>> x.append("hello")
>>> len(x)
6
>>> x[5]
"Hello"
>>> # can remove elements, defaults to popping off the last one
>>> x.pop()
>>> print x
>>> # can specify the index
>> x.pop(2)
>>> print x
>>> # can do a boolean check if something is in the list
>>> 5 in x
False
>>> 1 in x
```

### Exercise
```
- Create a list called `restaurants` consisting of the following elements in this order:
"Laut", "Random String", "Chipotle", "Eataly", "Sophie's Cuban", "Chop't", "Potbelly's"
- Get the third element of the list
- Add "Ootoya" to the end of the list
- Use .pop() to remove "Random String" from the list
- Print the list
- Check if 'Chipotle' is in the list
- Check if 'Random String' is in the list
- Get the length of the list
```

## Dictionaries (50)
Dictionaries are also massively useful. You can think of them as maps, between as set of keys and their corresponding values.
Let's look at one in the shell to better understand how they work and how they can be useful:

```python
>>> # Here's the syntax, {} with key:value, with key being a string.
>>> person = {"name": "John Jameson", "age": 31, "hobbies": ["tennis", "python", "piano"]}
>>> person["name"]
>>> # like a string, we use the brackets but instead of the index, we provide the key name
>>> person["age"]
>>> hobbies = person["hobbies"]
>>> len(hobbies)
>>> hobbies[1]
>>> person["random"]
KeyError
>>> person["location"] = "New York"
>>> person["deepest_darkest_secret"] = "Loves Vampire Diaries"
print person
>>> del person["deepest_darkest_secret"]
print person
>>> person.keys()
>>> person.values()
>>> person.items()
>>> # check if a key exists in the dictionary
>>> "name" in person
>>> "secret" in person
```
### Exercise
```
Create a dictionary called `class_data` with the following keys:
- "course_name", which should correspond to "Intro to Python"
- "student_count", which should correspond to number of students, say 20
- "instructor", which should itself be a dictionary with the following keys
    - "name" ("Suneel")
    - "gender" ("M")
    - "can_program" (True)
- get the student count from the dictionary
- get the instructor name from the dictionary
```

## If/Else (70)
If/else statements are blocks of our code that allow us to do different things based on some logical condition
Let's learn the syntax, note INDENTATION is important:
```python
>>> x = 5
>>> if x > 4:
        print "Hello"
    else:
        print "World"
Hello
>>> if x < 5:
        print "Less than five"
    else:
        print "Greater than or equal to five"
>>> if x == 1 or x == 2:
        print "Ha"
    elif x == 3:
        print "Hey"
    else:
        print "Hi"
```

### Exercise
```
Given x = "John Jameson",
- Construct an if else statement according to this logic: if "John" is in x, print "John is in x", otherwise print "John is not in x"
- Construct an if/elif/else statement according to this logic: if "roger" is in x, print "Hi Roger!", elif the length of x is greater than 20, print "thats a long string", else print "Oh well!"
```

## Loops (90)
Loops let us pass through a set of values and do some operation on each.
There are different kinds of loops, for loops and while loops. They're quite similar, but let's look at the canonical loop, the for loop.

### The modulo function
```python
>>> 4 % 2
>>> 5 % 2
>>> 6 % 2
>>> 7 % 2
>>> 10 % 5
>>> 11 % 5
```

What's happening here?

### For loop example

```python
>>> numbers = [1, 2, 8, 7, 9, 10]
>>> odds = []
>>> for dog in numbers:
        if dog % 2 == 1:
            odds.append(dog)

print odds
```
- the `dog` in the for loop syntax is a dummy variable that refers to the element in the list that we're passing through. The first time around, `dog` refers to 1, the last time it refers to 10.
- we are going through this list and if the number is odd, we add it to the odds list that we initialized before the for loop.

### A useful function: `range`
Before we move on to some practice problems, here is a useful function:
```python
>>> range(10)
```

### Exercise
- Construct a list of numbers between 0 and 1000 that are divisible by 33

## Functions (120)
Functions are the heart and soul of python. Functions are blocks of code that take an input and based on some rules produce an output.

Let's learn the syntax of functions:

```python
>>> def add(a, b):
        return a + b
>>> z = add(3, 4)
>>> print z
```
a and b are variables that the function `add` takes

### Exercises
- solo: create function `multiply` that takes two variables and returns their product
- with a partner: write a function that takes a list of numbers and return True if the sum of the numbers is even and False otherwise.

# Using Other Libraries (150)
What is a library? A reusable, collection of code that someone else (or you) has already written. Some great built-in libraries:
- `random`
- `csv`
- `collections`
- `datetime`

To use other libraries, we need to be able to:
- understand the documentation of that library
- understand what the inputs and outputs of their functions are
- how to call those functions correctly

Let's start with the random library.

## The `random` library.
Our first step is to locate the documentation. Google "python random". It should take you [here](https://docs.python.org/2/library/random.html)

Let's import the library
```python
>>> import random
>>> dir(random)
```

How does python know what `random` is and how to find the code? Because it comes built-in to the Python language. Other libraries such as `pandas` will have to be installed prior to use.

### Exercise 1
Find the `randint` function in the documentation and explain to your neighbor what it does and how to use it.

### Exercise 2
Again, with your partner, use the `randint` function to generate a random number between 1 and 125.

### Exercise 3
This time solo, use the `shuffle` function on this list: `[1, 2, 7, 5, 9, 10]`. What gets returned?

## What is `as`?
```python
>>> import random as rd
```

Let's see what happens...

# Intro to Pandas (175)
What is [pandas](http://pandas.pydata.org/pandas-docs/stable/)?

- analyze tabular data
- built on top of `scipy` and `numpy`, so quite fast
- incredibly powerful

## Our First DataSet
[Here](https://s3.amazonaws.com/python-level-2/sales-funnel.csv) is the data set.

### Exercise
With your partner, download the data and look at it in excel.

Questions:
- What is this dataset about?
- What are some questions you might ask about the data?

### Importing pandas
```python
>>> import pandas as pd
```

### Exercise
We want to read in the csv file. With your partner, look in the pandas documentation (or Google) to find out how to read in a csv file given a URL.
Then, read in the csv file from the above URL.

*Note*: We're going to be heavily commenting our code so that each step is super clear and we can refer back to it in the future and immediately understand what's being done.


### Questions
- How many different managers are there?
- What percentage of accounts in the sales funnel have been won?
- What is the total dollar amount pending?
-
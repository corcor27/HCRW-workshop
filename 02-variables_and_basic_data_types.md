---
title: Variables and basic data types
teaching: 35
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives
- Understand the syntax behind assigning values to variables in Python.
- Recognise common Python data types and understand why they matter.
- Understand that Jupyter notebooks run cells in the order you execute them, not the order they appear.
 
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What is a variable?
- What is a type?
- Why are types important?
- What happens when notebook cells are run out of order?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Variables

To do anything useful with data, we need to assign its value to a *variable*.
In Python, we can [assign](../learners/reference.md#assign) a value to a
[variable](../learners/reference.md#variable), using the equals sign `=`.
For example, we can track the weight of a patient who weighs 60 kilograms by
assigning the value `60` to a variable `weight_kg`:


:::::::::::::::::::::::::::::::::::::::::::: callout

In Python, `=` means assignment. It tells Python to store a value in a variable, it does not ask whether two things are equal. Later we will encounter `==` this is a check for equivalence.

::::::::::::::::::::::::::::::::::::::::::::



```python
weight_kg = 60
```

From now on, whenever we use `weight_kg`, Python will substitute the value we assigned to
it. In simple terms, a variable is a **name for a value**.

In Python, variable naming has rules:

* Variable names are case-sensitive (`My_name` is different from `my_name`).

* They can not contain spaces (e.g. `my name` =)  

* They must start with a letter or an underscore. 

* They can consist of letters, numbers, and underscores.  

* Some reserved words (e.g., `'else'`, `'for'`) cannot be used as variable names because they already have a specific meaning in Python.

This means that, for example:

- `weight0` is a valid variable name, whereas `0weight` is not
- `weight` and `Weight` are different variables

 
It may seem there are many restrictions but there are actually a huge number of variable naming combinations. However, just because you can use weird and wonderful combinations, doesn’t mean you should. There are several naming conventions in the Python community that help provide structure and consistency. 


1. my_variable (underscore or snake case) 

2. myVariable (camel case) 


Although some may violently disagree with us, we believe for most coders it does not matter which convention you pick. In Python, snake_case is the most common naming convention for variables, so it is a good default choice for beginners. More importantly, there are two key principles for variable naming that will make your life easier: 


1. ***Consistency*** - pick a convention and stick with it. 

2. ***Succinctness*** - Keep variable names short, readable, and descriptive. 


For ***example***, if you wanted a variable name for a temperature reading taken in Aberystwyth: 


This: 

>min_temp_aber_C 


Is better than this: 

>temp 
 

Or this: 

>theminimumtemperaturerecordedfromaberystwythindegreescelsius

 
Being consistent, aware of context, and conscious of your variable naming will make reading your code easier and decrease the risk of errors.


:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::: callout
WARNING: The first of many unfunny computer science jokes.

"There are only two hard problems in Computer Science: cache invalidation and naming things." -- Phil Karlton
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::


## Types of data

Python utilises different data types to efficiently store and manipulate different kinds of data. A type tells Python what kind of value something is, such as a whole number, a decimal number, or text. Python is dynamically typed, this means that you do not need to specify a data type when you declare a variable. You provide the variable name and the value you want to store, and Python handles the data type automatically. We will look at the most common data types in Python.
  
| Data Type       | Description                                     | Example                     |
|-----------------|-------------------------------------------------|-----------------------------|
| int             | Integer data type                               | 42                          |
| float           | Floating-point data type                        | 3.14                        |
| str             | String data type                                | 'hello'                     |
| bool            | Boolean data type                               | True, False                 |
| NoneType        | NoneType data type (represents null value)      | None                        |

In the example above, variable `weight_kg` has an integer value of `60`.
If we want to more precisely track the weight of our patient,
we can use a floating point value by executing:

```python
weight_kg = 60.3
```

To create a string, we add single or double quotes around some text.
To identify and track a patient throughout our study,
we can assign each person a unique identifier by storing it in a string:

```python
patient_id = '001'
```

## Built-in Python functions

To carry out common tasks with data and variables in Python,
the language provides us with several built-in [functions](../learners/reference.md#function).
To display information to the screen, we use the `print()` function:

```python
print(weight_lb)
print(patient_id)
```

```output
132.66
inflam_001
```

When we want to make use of a function, referred to as calling the function,
we follow its name by parentheses. The parentheses are important:
if you leave them off, the function doesn't actually run!
Sometimes you will include values or variables inside the parentheses for the function to use.
In the case of `print()`,
we use the parentheses to tell the function what value we want to display.
We will learn more about how functions work and how to create our own in later episodes.

We can display multiple things at once using only one `print()` call:

```python
print(patient_id, 'weight in kilograms:', weight_kg)
```

```output
inflam_001 weight in kilograms: 60.3
```

We can also call a function inside another
[function call](../learners/reference.md#function-call).
For example, Python has a built-in function called `type()` that tells you a value's data type:

```python
print(type(60.3))
print(type(patient_id))
```

```output
<class 'float'>
<class 'str'>
```

Moreover, we can do arithmetic with variables right inside the `print()` function:

```python
print('weight in pounds:', 2.2 * weight_kg)
```

```output
weight in pounds: 132.66
```

The above command, however, did not change the value of `weight_kg`:

```python
print(weight_kg)
```

```output
60.3
```

To change the value of the `weight_kg` variable, we have to
**assign** `weight_kg` a new value using the equals `=` sign:

```python
weight_kg = 65.0
print('weight in kilograms is now:', weight_kg)
```

```output
weight in kilograms is now: 65.0
```

## Using Variables in Python

Once we have data stored with variable names, we can make use of it in calculations.
We may want to store our patient's weight in pounds as well as kilograms:

```python
weight_lb = 2.2 * weight_kg
```

We might decide to add a prefix to our patient identifier:

```python
patient_id = 'inflam_' + patient_id
```

## How Python Assigns Data Types

### Dynamic Typing

In Python, you don’t declare a variable’s type explicitly. Instead, the type is determined automatically when you assign a value.

```python
x = 10        # x is an int
print(x)
x = "hello"   # now x is a string
print(x)
```

```python
10
hello
```
For example, depending on how you assign a value, Python automatically determines its type:

```python
a = 5
b = 5.0
c = "5"

print(type(a))  # int
print(type(b))  # float
print(type(c))  # str
```

```python
<class 'int'>
<class 'float'>
<class 'str'>
```


Different data types behave differently. Some can be combined directly, such as integers and floats, but others cannot. For example, strings cannot be added to numbers in a meaningful way without conversion.

Another challenge with dynamic typing is that sometimes values that look like numbers are actually stored as strings. This can lead to unexpected behaviour, as shown below:

```python
x = "10"        

```

To use this value as a number, we need to convert it from a string to an integer:

```python
print(type(x))       
x = int(x)
print(type(x))
```

```python
<class 'str'>
<class 'int'>
```

## Running code in order

Jupyter notebooks keep variables, imports, and results in memory as you run cells. That means each cell can depend on work done earlier. When cells are run out of order, the notebook can end up in a state where the code looks fine but behaves unpredictably.

### Running cells in order makes the notebook:

* easier to understand
* easier to debug
* easier for other people to reproduce
* less likely to break because of hidden state

A notebook is not just a document. It is also a live coding session.

If, during your work, you add something in cell 8 that cell 3 depends on, your notebook may still appear to work because both cells have already been run in your current session. However, if someone opens the notebook from scratch and runs the cells in order, they may get an error.

### Examples

```python
# Cell 1
x = 10
```

```python
# Cell 2
y = x + 5
print(y)
```
If Cell 2 is run before Cell 1, Python will raise an error because x does not exist yet.

### Problems caused by running out of order
* Name errors: variables or functions are missing
* Old values: variables keep outdated data from earlier runs
* Confusing bugs: results change for no obvious reason
* Poor reproducibility: others cannot get the same output
* Hidden dependencies: a cell works only because of some earlier unseen action

:::::::::::::::::::::::::::::::::::::::  challenge

## Check Your Understanding

What values do the variables `mass` and `age` have after each of the following statements?
Test your answer by executing the lines.

```python
mass = 47.5 #1
age = 122 #2
mass = mass * 2.0 #3
age = age - 20 #4
```

:::::::::::::::  solution

## Solution

```output
at 1 `mass` holds a value of 47.5, `age` does not exist
at 2 `mass` still holds a value of 47.5, `age` holds a value of 122
at 3 `mass` now has a value of 95.0, `age`'s value is still 122
at 4 `mass` still has a value of 95.0, `age` now holds 102
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: keypoints

- Basic data types in Python include integers, strings, and floating-point numbers.
- Use `variable = value` to assign a value to a variable in order to record it in memory.
- Variables are created on demand whenever a value is assigned to them.
- Use `print(something)` to display the value of `something`.
- Use `# some kind of explanation` to add comments to programs.
::::::::::::::::::::::::::::::::::::::::::::::::::



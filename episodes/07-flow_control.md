---
title: Flow control
teaching: 60
exercises: 30
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain what a `for` loop does.
- Correctly write `for` loops to repeat simple calculations.
- Write conditional statements including `if`, `elif`, and `else` branches.
- Correctly evaluate expressions containing `and` and `or`.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I do the same operations on many different values?
- How can my programs do different things based on data values?

::::::::::::::::::::::::::::::::::::::::::::::::::

Often, we want to perform different operations in our code based upon dynamic conditions. To explore this idea, we are going to pretend we have two sensors. The first represents temperature, and the second represents if there is rainfall or not. Our temperature value is numeric, and the rainfall variable is a boolean. To declare those variables, you can type:

```python
temp_reading = 16 

rainfall = True 
```

Then place the following code into your script:

```python
if rainfall == True: 
  print("Advise user to take an umbrella") 
```


Run the script using the run button (little green play button) above the script pane.

```python
Advise user to take an umbrella
```


From observing the output in the console and from a brief inspection of the code, it should be evident that we are evaluating the variable rainfall. Specifically, we are checking if it is True. If the outcome is of the check is true, then we perform any code within the indented block.

![](fig/ifflow1.png){alt='Flow diagram for if condition" caption="Figure 1: Flow diagram for an *if* condition'}



### if, else

Now modify your code to look like this:

```python
if rainfall: 
  print("Advise user to take an umbrella") 
else: 
  print("Leave your umbrella at home") 
```


Note: With boolean variables, we don't actually have to write `== True`.


![](fig/ifflow2.png){alt="Flow diagram for if condition" caption="Figure 2: Flow diagram for an if, else condition"}


### Change the condition
Now change the rainfall variable to False and run the script again.

```python
rainfall = False
```


```python
Leave your umbrella at home
```


Our code now reacts differently to different input values. You can combine if, elif (else if), and else statements to control the flow of your code.

### Conditional statements
* 'if' – Runs a block of code if a condition is true.
* 'elif' – Checks another condition if the previous `if` or `elif` condition was false.
* 'else' – Runs a block of code if none of the previous conditions were true.

### Comparison operators
We have encountered '==', which is used to check for equivalence. There are other comparison operators available to us.

* \> Greater than
* \>= Greater than or equal to
* < Less than
* <= Less than or equal to
* == Equal to
* != Not equal to

### Boolean operators

* **and**: Returns `True` only if both conditions are `True`.
* **or**: Returns `True` if at least one condition is `True`.
* **not**: Reverses a Boolean value, turning `True` into `False` and `False` into `True`.

Next:

```python
if rainfall or temp_reading < 10:
    print("Stay at home") 
else:
    print("Go outside")
```


By combining these operators, you can create sophisticated flow control mechanisms.

### For loops

In Python, a for loop is used to iterate over a sequence and perform a set of statements for each item in the sequence. Here is an example of a for loop in Python:

1. **Syntax:** The syntax of a for loop in Python is as follows:
   
   ```python
   for item in sequence:
       # Statements to execute for each item
   ```

2. **Explanation:** 
   - The `for` keyword is used to start the loop.
   - `item` is a variable that takes each value from the `sequence` in each iteration of the loop.
   - `sequence` is the collection of items over which the loop iterates.
   - Indentation is used to define the block of statements to be executed for each iteration of the loop.   


3. **Examples:** Here's an examples of a for loop that iterates over a range of numbers and prints each number:
   
```python
   for i in range(5):
       print(i)
```
{: .language.python}

```python
0
1
2
3
4
```


 Here's an examples of a for loop that iterates over a list of strings and prints each string:

```python
days = ['monday','tuesday','wednesday','thursday','friday']

for day in days:
    print(day)
```

  
```python
monday
tuesday
wednesday
thursday
friday
```


For loops are commonly used in Python for iterating over sequences, performing repetitive tasks, and processing collections of data.

### Keeping things clear
It is possible to put conditional statements inside conditional statements these are then referred to as 'nested'. If your code becomes overly nested it can impact readability and maintainability. It is good practice to keep your workflow as simple as possible, this can be made easier by spending time on design and regular refactoring.

Note: Refactoring is the process of restructuring code, not to change the functionality but to improve factors like readability, maintainability, efficiency.

We've covered a very basic introduction to flow control in Python, but there are many more facets to explore in order to fully understand all possibilities. Please feel free to check out the link below for more information on flow control.


[Python control flow tutorial](https://docs.python.org/3/tutorial/controlflow.html)


:::::::::::::::::::::::::::::::::::::::: keypoints

- Use `for variable in sequence` to process the elements of a sequence one at a time.
- Don't forget to indent.
- You can use `len(thing)` to determine the length of something that contains other values.
- Use `if condition` to start a conditional statement, `elif condition` to provide additional tests, and `else` to provide a default.
- Use `==` to test for equality and `=` for assignment.
- In Python, some values are treated as false in conditions, including `\0`, `''`, `[]`, and `None`.
::::::::::::::::::::::::::::::::::::::::::::::::::



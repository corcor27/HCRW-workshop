---
title: Libraries and imports
teaching: 15
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Install and import libraries.
- Understand how libraries relate to environments.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- Why do we need libraries?
- What does `import ... as ...` do?

::::::::::::::::::::::::::::::::::::::::::::::::::


## What is a library?

A library is a collection of ready-made code written by other programmers that you can use in your own program.

Instead of building every tool yourself, you can borrow tools that already exist. A library might contain code for:

* doing calculations
* working with data
* drawing graphs
* making games
* handling dates and times

You can think of a library like a toolbox.
If you need a hammer, you do not make one from metal and wood first, you take one from the toolbox and use it.
In programming, a library is that toolbox.

## Why do programmers use libraries?

Programmers use libraries because they save time and effort.

If somebody has already written code that works well, it makes sense to use it rather than create the same thing again. Libraries help us:

* work faster
* avoid repeating work
* use tested and reliable code
* solve bigger problems more easily

This is one reason programming is powerful: we build on work that already exists.

## Why do we not write everything from scratch?

Writing everything from scratch would take far too long and would often lead to more mistakes.

Imagine you wanted to create a graph, analyse a large dataset, or generate random numbers. You could try to write all that code yourself, but it would be slow, difficult, and unnecessary.

Instead, we use libraries because:

* they are already written
* they are usually tested by many people
* they let us focus on solving the actual problem
* they make programs shorter and clearer

So rather than spending hours rebuilding common tools, we use libraries and spend our time on the parts that are unique to our project.

## What does import mean?

To use a library in Python, we usually import it.


:::::::::::::::::::::::::::::::::::::::::::::::::::: callout

If you have never used Python before, or if you are not using the Carpentries environment, you may need to install some packages first.

```python
%pip install [PACKAGE NAME]
```

::::::::::::::::::::::::::::::::::::::::::::::::::::


The word import tells Python to load the library so we can use its tools in our code.

For example:

```python
import math
```

This imports the math library, which contains useful mathematical functions.

After that, we can use parts of the library like this:

```python
print(math.sqrt(16))
```

This prints the square root of 16.

## What does import ... as ... mean?

Sometimes library names are long, or programmers want a shorter name to type.
Python lets us rename a library when we import it.

For example:

```python
import numpy as np
```

This imports the library numpy but gives it the shorter name np inside our code.

Now instead of writing:

```python
numpy.array([1, 2, 3])
```

we write:

```python
np.array([1, 2, 3])
```

This is quicker and easier to read once you know the shortcut.

### Why use import ... as ...?

We use import ... as ... because:

* it saves typing
* it makes code neater
* short names are often standard and widely recognised

For example:

* numpy as np
* pandas as pd
* matplotlib.pyplot as plt

These short versions are commonly used, so using them can make code easier for others to recognise.


## Packages, versions, and environments

Packages are updated over time, so different versions of the same package can behave differently.

In simple projects this may not matter much, but larger projects often depend on several packages at once. These dependencies can require specific versions to work correctly together.

To manage this, programmers often use an **environment**. An environment is a separate space that stores the Python version and package versions needed for one project.

This helps us make sure we have the right setup for our code and avoids conflicts between different projects.

## Getting help with libraries

If you’re getting started with NumPy and pandas, there are plenty of accessible ways to find help and build confidence. Official documentation is often the best first stop—both libraries provide clear guides, tutorials, and examples that cover everything from basic usage to advanced features.

For example NumPy can be found at: https://numpy.org/

Or Pandas at https://pandas.pydata.org/

Online communities are also incredibly useful. Platforms like Stack Overflow, Reddit, and specialised data science forums allow you to search for answers to common problems or ask your own questions. Chances are, someone else has already run into (and solved) the same issue.

For more structured learning, consider free courses and video tutorials on sites like YouTube, Coursera, or Kaggle. These often walk through real-world examples and can make complex concepts easier to understand.

Finally, don’t underestimate the value of experimentation. Try small projects, test out functions, and read error messages carefully, they often point you in the right direction. With consistent practice and the wealth of resources available, getting comfortable with NumPy and pandas becomes much more manageable.

:::::::::::::::::::::::::::::::::::::::: keypoints

- Libraries give us access to code that other people have already written.
- We import libraries so we can use their tools.
- We sometimes rename them with as to make our code shorter and easier to work with.
- We use environments to manage package versions as our projects get more complicated. 

::::::::::::::::::::::::::::::::::::::::::::::::::



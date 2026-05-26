---
title: Pathing and workspaces
teaching: 30
exercises: 30
---

::::::::::::::::::::::::::::::::::::::: objectives

* explain where a notebook is stored
* explain where data files are stored
* use relative paths
* load a CSV file
* load an image file
* load an audio file
* spot and fix common file and path mistakes


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How do I know what Python can "see"?
- Where am I working?
- Where are my outputs going?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Files, Folders, and Paths

### What are files, folders, and paths?

A file is a single item stored on a computer, such as:

* a notebook
* a CSV file
* an image
* an audio file

A folder contains files and sometimes other folders.

A path is the set of directions that tells the computer where a file is located in the folder structure. A path identifies an item in a hierarchical file system.

Analogy

Think of a computer like a building:

* folders are rooms
* files are objects inside the rooms
* a path is the directions to reach one object

For example:

```python
project/data/sales.csv
```
This means:

* go to the project folder
* then the data folder
* then find the file sales.csv

### Where is the notebook?

A Jupyter notebook is itself a file, usually ending in .ipynb.

That means the notebook lives in a folder somewhere on your computer, just like any other file. In Jupyter, the notebook runs relative to a current working directory, and relative paths depend on that location.

### Important idea 

When you write code to open a file, Python needs to know:

“Starting from where?”

Usually, that starting point is the current working directory, which is often the same as the notebook's folder.

So if your notebook is in:

```python
project/
    analysis.ipynb
```
then the notebook is inside the project folder.

### Where is the data?

Your data is stored as separate files somewhere in your folders.

For example:

```python
project/
    analysis.ipynb
    data/
        sales.csv
        cat.jpg
        song.wav
```
Here:

* the notebook is analysis.ipynb
* the data files are inside the data folder

This is a very common and sensible structure because it keeps the notebook and data organised. Good project structure makes work easier to repeat and understand.

### Relative paths

A relative path gives directions from the current notebook location, rather than from the very top of the computer. Relative paths assume you are starting in the current working directory.

Example folder structure

```python
project/
    notebook.ipynb
    data/
        marks.csv
```
If the notebook is in project/ and the file is inside data/, the relative path is:

```python
"data/marks.csv"
```

This means:

* from where the notebook is now
* go into the data folder
* open marks.csv

Why relative paths are useful

Relative paths are better for classwork and projects because:

* they are shorter
* they are easier to read
* they work better when a project folder is moved to another computer

## Some additional file types

### Loading an image

One common way to load an image is with PIL:

```python
from PIL import Image

img = Image.open("../additional_stuff/cat.jpg")
img.show()
```

This opens the image file from the data folder.

You can also use a library called OpenCV.

```python
import cv2

img = cv2.imread("../additional_stuff/cat.jpg")
cv2.imshow("Image", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

Another common option in notebooks is matplotlib:

```python
import matplotlib.pyplot as plt
import matplotlib.image as mpimg

img = mpimg.imread("../additional_stuff/cat.jpg")
plt.imshow(img)
plt.axis("off")
```

### Loading an audio file

A simple notebook-friendly way is to use IPython display tools:

```python
from IPython.display import Audio

filename = "../additional_stuff/03-01-01-01-01-02-01.wav"
Audio(filename)

```
This loads the audio file and gives you a player in the notebook.

We can visualise the audio using tools we have already encountered and a new libraries (scipy).

```python
from scipy.io import wavfile

sample_rate, data = wavfile.read(filename)

plt.figure(figsize=(10, 3))
plt.plot(data)
plt.ylabel("Amplitude")
plt.show()
```

### Troubleshooting / debugging path problems

When a file will not load, students should ask:

* Where is my notebook?
* Where is my file?
* What path am I giving Python?
* Is the filename spelled correctly?
* Is the extension correct?
* Am I using the right folder names?

A helpful debugging command is:

```python
import os
print(os.getcwd())
print(os.listdir())
```

This shows:

* the current folder
* the files and folders inside it


:::::::::::::::::::::::::::::::::::::::: keypoints

- Be aware of your current working directory
- One of the biggest struggle for importing your data into Python is getting the paths correct.

::::::::::::::::::::::::::::::::::::::::::::::::::



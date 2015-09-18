# A Very Brief Introduction to Python
This document is not a Python tutorial but a quick introduction to the basic concepts and terms you need to learn Python. You can do some pretty powerful stuff quite easily by copying other people's code, but you'll need to have an idea of what you are looking at if you want to catch mistakes or adapt the code for your own purposes. Once you've read through this material, you should be able to understand online tutorials discussions. If you want to learn from a tutorial, I recommend [Learn Python the Hard Way](http://learnpythonthehardway.org/book/) (the bit about "the hard way" is ironic--it's very easy).

### Scripts
In computer programming, there is no clear distinction between and a script. Typically the latter has a smaller, less elaborate code base than the former. In the Digital Humanities, you'll hear about practioners writing scripts accomplish certain tasks. If the code is an integrated set of functions or is accompanied by a web-based or graphic user interface (GUI), it is more likely to be referred to as a tool. The term "app" has not yet caught on in this area of practice. 

### Python packages
Python has a base library of functions, which can be extended by importing packages. Packages are libraries of functions created by third parties for specific taks, but some of these tasks are so common that the packages used for them are ubiqitous in Python scripts. Packages have to be downloaded and installed in Python, after which they are generally imported with the command `import PACKAGE_NAME`. Python "distributions" like Anaconda come with many common packages pre-installed.

### Data Types
Some functions can only be used on certain types of content. In Python, some of the most common types of content are *numbers*, *strings*, *lists*, and *dictionaries* (also known as "dicts"). Content is defined as one content type or the other the use of different delimiter symbols:

* numbers: no delimiters (e.g. `100`)
* strings: enclosed in apostrophes or quotation marks (e.g. `'John'` or `"John"`). Word processor style smart quotes or curly quotes cannot be used as string delimiters and will be interpreted as part of the string.
* lists: enclosed in square brackets (e.g. `[1, 2]` or `['Jack', 'Jill']`).
* dicts: enclosed in curly brackets (e.g. {'Jack': 1}).

### Strings
Strings contain alphanumeric data--that is, either numbers or letters, as well as punctuation marks. Quotation marks inside of apostrophe delimiters will be interpreted as part of the string, as will apostrophes inside quotation mark delimiters. For example, you could encode the sentence *He said, "We are ready."* as `'He said, "We are ready."'` The sentence *We're ready.* could be encoded `"We're ready."` But for *He said, "We're ready."* you would probably have to "escape" one the punctuation marks. The easiest method would be like this: `'He said, "We\'re ready."'` The backslash before the apostrophe tells Python not to interpret it as a string delimiter.

### Numbers
Various types of numbers are recognised by Python. The most important types are floating points, which can have decimal points, and integers, which cannot. There functions to convert one to the other.

### Lists
Lists are comma-separated items belonging to other data types such as numbers or strings, as in the examples above. You can also have lists of dictionaries, or even lists of lists. You can reference items in a list by a number in square brackets. For instance, if you had a list called `myList`, you could get the first item in the list with `myList[0]`. This also illustrates the fact that Python starts counting from 0, rather than 1. Note that strings are really lists of letters. You can see this if you try the following code:

```python
string = "Hello"
print(string[0])
```
You will get "H" as the result.

### Dictionaries
Dictionaries are like lists, except that each item is a key-value pair (separated by a colon). A common use of dictionaries is to contain word counts. Consider this list of dictionaries: `[{'Jack': 1}, {'Jill': 2}]`. This might be used to indicate that the word "Jack" occurs once and the word "Jill" occurs twice.

### Concatenation
Two strings can be combined, or **concatenated**, with the use of the `+` sign. For example, `"John " + "Smith"` will produce the string `"John Smith"`. Numbers cannot be concatenated with string unless you first "cast" them as a string with the `str()` function. For instance, `"John " + "Smith" + str(1)` will produce the string `"John Smith1"`.

Two lists can also be combined through concatenation. For instance, `[1, 2, 3] + [4, 5, 6]` would produce `[1, 2, 3, 4, 5, 6]`.

### Variables
A variable is a container for some data of any type. This container is referenced by a label or variable name. Content is assigned to a variable using the `=` sign. For instance, `firstname = "John"` would assign the string `"John"` to the variable `firstname`. If you also assigned `lastname = "Smith"`, then `firstname + " " + lastname` would produce the string `"John Smith"`. In some cases, you have to create the variable before you assign a value to it. For instance, you might create an empty list like `myList = []`.

### Functions
A function is a command to do something with one of the data types and produce a result. Functions are identified by function names followed by parentheses. We have seen an example above of the `str()` function, which converts a number like 1 to a string. Notice that you place the item you wish to convert to a string inside the parentheses. The value in parentheses is called the *argument*. You can use a variable as the argument of a function. For instance, if you defined `myvar = 1`, you could then use `str(myvar)`. Another example is the `append()` function, which adds an item to a list. For instance, you could add the number 1 to the `myList` created above: `myList.append(1)`.

As mentioned earlier, Python has a set of built-in functions like `str()` and `append()`, and more functions can be imported from packages. However, sometimes you will want to define your own. Here's a small script to show how this is done.

```python
myList = []

def addToList(item):
	item = str(item)
	myList.append(item)

addToList('John')
addToList(1)
```

The script starts with an empty list. It then defines a function called `addToList()`. Finally, it "calls" the function, first using the name John and then again using the number 1. Since these belong to different data types, we might want to ensure that every item in our list is a string. So within the function, we call use the `str()` function to cast the item submitted as the function's argument to a string. Then we use the `append()` function to add it to the list.

We don't *have to* define a function for this; we could just repeat our string conversion and list appending code for each item, but calling them in a function avoids repeating code and keeps our code organised.

It is useful to look at one more example:

```python
def convertNumber(item):
	item = str(item)
	return item

myNumericString = convertNumber(1)
```
This wins the award for the most pointless function ever. You can achieve the same result with `myNumericString = str(1)`. But the `convertNumber()` function does illustrate an important point. The result of a function can be "returned" to the main code block with the `return` command, and this can be assigned to a new variable.

### Indentation
In Python, code that is part of a function must be indented by four spaces. Some editors may be set to treat a tab as equivalent to four spaces; this is something you can test. If you get the indentation wrong, you will receive an error. if you are used to other coding languages, it may take some time to get used to the fact that indentation matters in Python.

### Loops
A loop is a function that iterates through items in (typically) a list. Here is an example:

```python
myList = [1, 2, 3]
for item in myList:
	item = "item" + str(item)
	print(item)
```
The "for" loop goes through each number in the list, concatenates it with the string `"item"` after first converting the number to a string, and then prints the result.

Python has more specialised methods of looping through lists, as well as methods of looping through the key-value pairs of dictionaries. These methods can be learnt easily through Google searches.


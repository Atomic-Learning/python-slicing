Slicing allows you to extract a portion of a collection indexed with integers, such as a string, list, tuples and Numpy arrays. The same syntax applies for all types. Here, we'll use lists and strings as an example.

# Basic Slicing: [start:stop]

The slice notation `[start:stop]`{.python} extracts characters from index `start`{.python} up to (but **not including**) index `stop`{.python}:

```py-cell
word = "hello"
#       01234

print(word[0:3])
print(word[1:4])
print(word[0:5])
```

Notice: `stop`{.python} is **exclusive** (not included), so `[0:3]`{.python} gives indices 0, 1, 2 but not 3. When slicing a string, the returned value is a new string of the extracted characters.

# Default Values

If you omit `start`{.python}, it defaults to 0. If you omit `stop`{.python}, it defaults to the end of the string:

```py-cell
my_list = [0, 10, 20, 30, 40]
#         0   1   2   3   4

print(my_list[:3])
print(my_list[3:])
print(my_list[:])
```

This can be particularly useful when asking for things like "the first three items" or "the last two items"{.python}.

When slicing a list, the returned value is a new list of the extracted elements.

# Adding a Step: [start:stop:step]

The `step`{.python} parameter controls which characters are included. A step of 2 means "take every other character" when slicing a string:

```py-cell
string = "Pythonic"
#         01234567

print(string[0:6:2])
print(string[1:6:2])
print(string[::3])
```

If you omit `step`{.python}, it defaults to 1 (every character):

```py-cell
string = "An example"

print(string[0::])
print(string[1:5:])
```

# Negative Indices in Slices

You can use negative indices in slices:

```py-cell
my_list = [0, 1, 2, 3, 4, 5]

print(my_list[-3:-1])
print(my_list[0:-1])
```

When using a negative step, `start`{.python} will typically be higher than `stop`{.python}. If `start`{.python} is omitted, it defaults to the end of the string and, if `stop`{.python} is omitted, it defaults to the beginning of the string.

```py-cell
message = "Hello there!"

print(message[-2::-3])
print(message[8::-3])
```

# Out of Range Indices

If `start`{.python} or `stop`{.python} are out of bounds, an exception will not be raised:

```py-cell
string = "Slicing"
print(string[0:100])  # No error even though index 100 doesn't exist
```

In these cases, Python will return whatever characters or items are available within the bounds of the string or list.

# Empty Return Values

There are several situations where an empty slice is returned:

* When `step`{.python} is positive (or omitted) and `start`{.python} is greater than or equal to `stop`{.python}, e.g., `"hello"[3:1]`
* When the slice is out of bounds, e.g., `"hello"[10:20]{.python}`
* When the `step`{.python} is negative and `start`{.python} is less than or equal to `stop`{.python}, e.g., `"hello"[1:3:-1]`

For example:

```py-cell
print("hello"[3:1])
print("hello"[10:20])
print("hello"[1:3:-1])
```
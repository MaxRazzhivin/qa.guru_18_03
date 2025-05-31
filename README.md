# Some useful materials for myself

## Working with float variables to avoid mistakes with operations like 0.1 + 0.2 == 0.3 better to use library Decimal:

```bash
from decimal import Decimal 
```

## Working with random values

```bash
import random
random.randint(0,100) - return random value in range from 0 till 100, include 100 
```

### We can fix value from first return of above function by random.seed('some word')

```bash
random.seed('some word')
random.randint(0,100) - make random value only once and allow to use with assert in future
```

```bash
random.choice() - return random value from list, tuple or string 

Examples: 

fruits = ['apple', 'banana', 'cherry', 'orange']
random_fruit = random.choice(fruits)

word = "Python"
random_letter = random.choice(word)

colors = ('red', 'green', 'blue', 'yellow')
random_color = random.choice(colors)
```

### Library Faker for generating fake data. It can generate a variety of data types, including names, addresses, emails, dates, and much more.

```bash
pip install Faker
```

```bash
from faker import Faker

# Create a Faker instance
fake = Faker()

# Generate a random name
random_name = fake.name()
print(f"Random Name: {random_name}")
```

```bash
from faker import Faker

fake = Faker()

# Generate a random address
random_address = fake.address()
print(f"Random Address:\n{random_address}")
```

### You can generate multiple profiles using the profile() method

```bash
from faker import Faker

fake = Faker()

# Generate multiple fake profiles
for _ in range(5):
    profile = fake.profile()
    print(profile)
```

### Generating Fake Company Information

```bash
from faker import Faker

fake = Faker()

# Generate a random company name and job title
company_name = fake.company()
job_title = fake.job()
print(f"Company: {company_name}, Job Title: {job_title}")
```

### Generating Fake Data in Different Locales

```bash
from faker import Faker

# Create a Faker instance for French locale
fake_fr = Faker('fr_FR')

# Generate a random name in French
random_name_fr = fake_fr.name()
print(f"Random French Name: {random_name_fr}")
```

### Generating Fake Data for Testing (with Pandas in the end)

```bash
pip install pandas
```

```bash
from faker import Faker
import pandas as pd

fake = Faker()

# Create a list of fake data
data = []
for _ in range(10):  # Generate 10 records
    data.append({
        'Name': fake.name(),
        'Address': fake.address(),
        'Email': fake.email(),
        'Date of Birth': fake.date_of_birth(),
    })

# Create a DataFrame from the data
df = pd.DataFrame(data)
print(df)
```

## Working with .round() - function is used to round a floating-point number to a specified number of decimal places

```bash
round(number, ndigits)
• number: The number you want to round.
• ndigits: (Optional) The number of decimal places to round to. If omitted, it defaults to 0, meaning the number will be rounded to the nearest integer.

print(round(3.14159))      # Output: 3
print(round(3.14159, 2))   # Output: 3.14
print(round(3.14159, 3))   # Output: 3.142

print(round(5.5))          # Output: 6 (rounds to the nearest even number)
print(round(4.5))          # Output: 4 (rounds to the nearest even number)

print(round(-2.5))         # Output: -2
print(round(-2.6))         # Output: -3
```

## Too long line of code - how to carefully for eyes make breakdown and save readability of code

If you need to break a line, you can use the backslash `\`, but this is not the most preferred method, as it can reduce
readability:

``` bash
long_variable_name = some_function(arg1, arg2, arg3) + \
                     another_function(arg4, arg5)
```

```bash
or \n with any text like "Hello, \nworld!"
or raw-string, if we want to see each symbol like "\n":
  r"Hello, \nworld!" -> it will return "Hello, \nworld!"
```

## Strings

```bash
str.lower() -> Converts all characters in the string to lowercase
str.upper() -> Converts all characters in the string to uppercase
str.title() -> Converts the first character of each word to uppercase and the rest to lowercase

str.strip() -> Converts the first character of each word to uppercase and the rest to lowercase
  s = "   Hello World   "
  print(s.strip())  # Output: "Hello World"
  
str.split() -> Splits the string into a list based on a specified delimiter (default is whitespace)
  s = "Hello World"
  print(s.split())  # Output: ['Hello', 'World']

str.join() -> Joins elements of an iterable (like a list) into a single string with a specified separator

  words = ['Hello', 'World']
  print(' '.join(words))  # Output: "Hello World"
  
str.replace(old, new) -> Replaces occurrences of a substring with another substring
    s = "Hello World"
    print(s.replace("World", "Python"))  # Output: "Hello Python"
    
str.find(sub) -> Returns the lowest index of the substring if found, otherwise returns -1.
  str = "Hello World"
  print(str.find("World"))  # Output: 6

str.startswith(prefix) -> Checks if the string starts with the specified prefix, return True of False
  str = "Hello World"
  print(str.startswith("Hello"))  # Output: True
      
str.endswith(suffix) -> Checks if the string ends with the specified suffix
  str = "Hello World"
  print(str.endswith("World"))  # Output: True
```

### String formatting

```bash
• f-strings (formatted string literals): A way to embed expressions inside string literals, using curly braces {}.
name = "Alice"

  age = 30
  print(f"{name} is {age} years old.")  # Output: "Alice is 30 years old."
  
• str.format(): Another way to format strings by using placeholders.

print("{} is {} years old.".format(name, age))  # Output: "Alice is 30 years old."

One more example of .format: 

url_template = 'https://yourservice.com/v1/api/{}'
users_url = url_template.format('users') -> https://yourservice.com/v1/api/users_url
groups_url = url_template.format('groups') -> https://yourservice.com/v1/api/groups_url

Also if we write f-string like this: 
  print(f"{name=}, {age=}!") -> return name='Alice', age=30!
```

### String testing methods

```bash
• str.isalpha(): Returns True if all characters in the string are alphabetic.

• str.isdigit(): Returns True if all characters in the string are digits.

• str.isalnum(): Returns True if all characters are alphanumeric.
```

## List functions

```bash
list.append(item) - Adds an item to the end of the list

  my_list = [1, 2, 3]
  my_list.append(4)
  print(my_list)  # Output: [1, 2, 3, 4]

list.extend(iterable) - Extends the list by appending elements from an iterable (like another list)

  my_list.extend([5, 6])
  print(my_list)  # Output: [1, 2, 3, 4, 5, 6]
  
list.insert(2, "a") - Inserts an item at a specified index

  my_list.insert(2, 'a')
  print(my_list)  # Output: [1, 2, 'a', 3, 4, 5, 6]

list.remove(item) - Removes the first occurrence of an item from the list

  my_list.remove('a')
  print(my_list)  # Output: [1, 2, 3, 4, 5, 6]

list.pop(index) - Removes and returns the item at the specified index (or the last item if no index is specified)

  last_item = my_list.pop()
  print(last_item)  # Output: 6
  print(my_list)    # Output: [1, 2, 3, 4, 5]
  
list.index(item) - Returns the index of the first occurrence of an item in the list

  index_of_3 = my_list.index(3)
  print(index_of_3)  # Output: 2

list.count(item) - Returns the number of occurrences of an item in the list

  count_of_2 = my_list.count(2)
  print(count_of_2)  # Output: 1

list.sort() - Sorts the items of the list in place (ascending order by default)

  my_list.sort()
  print(my_list)  # Output: [1, 2, 3, 4, 5]

list.reverse() - Reverses the elements of the list in place

  my_list.reverse()
  print(my_list)  # Output: [5, 4, 3, 2, 1]
    
```

## List comprehensions - List comprehensions provide a concise way to create lists. They can be used for transforming and filtering items in a list

```bash
squared = [x**2 for x in range(10)]   # Creates a list of squares from 0 to 9
print(squared)                         # Output: [0, 1, 4, 9, ..., 81]

even_numbers = [x for x in range(20) if x % 2 == 0]   # List of even numbers
print(even_numbers)                   # Output: [0, 2, ..., 18]

```

## Set is a powerful data structure that provides a collection of unique elements

```bash
You can create a set using curly braces or the set() constructor.

     my_set = {1, 2, 3}
     another_set = set([1, 2, 3, 4])
     
     
.add(element): Adds a single element to the set

     my_set.add(4)

.update(iterable): Adds multiple elements from an iterable (like a list or another set)

     my_set.update([5, 6])

.remove(element): Removes an element from the set. Raises a KeyError if the element is not found

     my_set.remove(4)

.discard(element): Removes an element from the set if it exists. Does not raise an error if the element is not found.

     my_set.discard(10)  # No error even though 10 is not in the set
     
.clear(): Removes all elements from the set

     my_set.clear()

```

## Set Operations:

```bash
Union: .union(other_set) or | operator: Combines elements from both sets

     set1 = {1, 2, 3}
     set2 = {3, 4, 5}
     union_set = set1.union(set2)  # {1, 2, 3, 4, 5}
     
Intersection: .intersection(other_set) or & operator: Returns common elements.

     intersection_set = set1.intersection(set2)  # {3}
     
Difference: .difference(other_set) or - operator: Returns elements in the first set but not in the second.

     difference_set = set1.difference(set2)  # {1, 2}
     
Symmetric Difference: symmetric_difference(other_set) or ^ operator: Returns elements in either set but not in both.

     symmetric_diff_set = set1.symmetric_difference(set2)  # {1, 2, 4, 5}
     
Membership Testing - You can check if an element is in a set using the in keyword:

     if 1 in my_set:
         print("1 is in the set")
     
Length of a Set - Returns the number of unique elements in the set

     length = len(my_set)

Copying a Set - Creates a shallow copy of the set.

     new_set = my_set.copy()

Frozenset - Creates an immutable version of a set, which can be used as a key in dictionaries.

     immutable_set = frozenset([1, 2, 3])
      
```

## Dictionaries - a built-in data structure that allows you to store data in key-value pairs. They are unordered, mutable, and indexed, which makes them very versatile for various programming tasks.

```bash
Creating a Dictionary - you can create a dictionary using curly braces {} or the dict() constructor.

my_dict = {'key1': 'value1', 'key2': 'value2'}
another_dict = dict(key1='value1', key2='value2')

Accessing Values - you can access values in a dictionary using their keys.

value = my_dict['key1']  # Returns 'value1'

Adding or Updating Key-Value Pairs - you can add new key-value pairs or update existing ones by assigning a value to a key

my_dict['key3'] = 'value3'  # Adds a new key-value pair
my_dict['key1'] = 'new_value'  # Updates the value for 'key1'

```

### Removing Key-Value Pairs: 

```bash
.pop(key) - Removes the specified key and returns its value. Raises a KeyError if the key is not found.

  value = my_dict.pop('key2')  # Removes 'key2' and returns its value
  
.popitem(): Removes and returns the last inserted key-value pair as a tuple. Useful for LIFO (Last In, First Out) operations.

  last_item = my_dict.popitem()  # Returns ('key3', 'value3')

del statement: Deletes a key-value pair

  del my_dict['key1']  # Deletes the entry with key 'key1'
  
```

### Clearing the Dictionary

```bash
.clear() - Removes all items from the dictionary

  my_dict.clear()  # The dictionary is now empty
  
```

### Checking for Keys

```bash
in keyword: Checks if a key exists in the dictionary.

  if 'key1' in my_dict:
      print("Key exists")
  
```

### Getting Values

```bash
.get(key, default=None): Returns the value for the specified key if it exists; otherwise, returns the default value (None if not specified).

  value = my_dict.get('key4', 'default_value')  # Returns 'default_value'
  
```

### Dictionary Comprehension

```bash
You can create dictionaries using comprehension for concise syntax

squared_dict = {x: x**2 for x in range(5)}  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

### Iterating Through a Dictionary

```bash
You can iterate through keys, values, or key-value pairs:

Keys:

  for key in my_dict:
      print(key)
  
Values:

  for value in my_dict.values():
      print(value)
  
Key-Value Pairs:

  for key, value in my_dict.items():
    print(key, value)
  
```
### Copying a Dictionary:

```bash
.copy(): Creates a shallow copy of the dictionary.
new_dict = my_dict.copy()
```

### Merging Dictionaries:

```bash
.update(other): Updates the dictionary with elements from another dictionary or iterable of key-value pairs.
my_dict.update({'key4': 'value4', 'key5': 'value5'})
```

### Length of a Dictionary:

length = len(my_dict) - Returns the number of key-value pairs in the dictionary

### Nested Dictionaries:

```bash
Dictionaries can contain other dictionaries as values, allowing for complex data structures.

nested_dict = {
    'outer_key': {
        'inner_key1': 'inner_value1',
        'inner_key2': 'inner_value2'
    }
}
```

## Mutability - in Python refers to the ability of an object to be changed after it has been created

### Mutable objects can be modified in place. This means that their contents can be changed without creating a new object. Common mutable types in Python include:

```bash
Lists: You can add, remove, or change elements

  my_list = [1, 2, 3]
  my_list.append(4)  # List is now [1, 2, 3, 4]
  my_list[0] = 10    # List is now [10, 2, 3, 4]
  
For making separate list we should make real copy of list:

  l2 = l1.copy()
  l2.append(4) - by this we make l2 copy and l1 should be not changed
  
If our list contains additional list, set or dict inside we should use .deepcopy() to copy all data: 
  from copy import deepcopy
  l3 = deepcopy(l2)

Dictionaries: You can add, remove, or change key-value pairs

  my_dict = {'a': 1, 'b': 2}
  my_dict['c'] = 3    # Dictionary is now {'a': 1, 'b': 2, 'c': 3}
  my_dict['a'] = 10   # Dictionary is now {'a': 10, 'b': 2, 'c': 3}

Sets: You can add or remove elements

  my_set = {1, 2, 3}
  my_set.add(4)       # Set is now {1, 2, 3, 4}
  my_set.remove(2)    # Set is now {1, 3, 4}
```

### Immutable Objects - cannot be changed after they are created. Any modification will result in the creation of a new object. Common immutable types in Python include:

```bash
Tuples: Once created, you cannot change the elements of a tuple.

  my_tuple = (1, 2, 3)
  # my_tuple[0] = 10    # This will raise a TypeError
  
Strings: Strings cannot be modified; any operation that seems to modify a string will actually create a new string.

  my_string = "hello"
  new_string = my_string.upper()   # Creates a new string 'HELLO'

Frozensets: Like sets but immutable

  my_frozenset = frozenset([1, 2, 3])
  # my_frozenset.add(4)   # This will raise an AttributeError
  
```
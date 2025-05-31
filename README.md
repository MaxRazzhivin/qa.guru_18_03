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
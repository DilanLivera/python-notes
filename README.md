# Python Notes

[Python documentation](https://docs.python.org/3/)

### Dictionary
Dictionaries are key value pairs and list are ordered list of elements.

- To create a dictionary
  ```Python
  cat = { "name": "blue", "age": 3.5 }
  ```
  or
  ```Python
  cat = dict( name = "blue", age = 3.5 )
  ```

- To Access data from a dictionary
  ```Python
  cat["name"] # 'blue'
  ```

- To iterate
  ```Python
  # iterate through keys
  for key in cat.keys()
    print(key)

  # iterate through values
  for value in cat.values()
    print(value)

  # dict.items() returns a list of tuples
  for key,value in cat.items()
    print(key,value)
  ```

- To check does a dictionary have a key
  ```Python
  "name" in cat # True
  ```

- To check if value exist in the dictionary
  ```Python
  "blue" in cat.values() # True
  ```

- Dictionary Comprehension **`{ __:__ for __ in __ }`**
  ```Python
  numbers = dict( first = 1, second = 2, third = 3)

  { key: value ** 2 for key,value in numbers.items() } # { 'first': 1, 'second': 4, 'third': 9 }

  { num: num**2 for num in [1,2,3,4,5] } # { 1: 1, 2: 4, 3: 9, 4: 16, 5: 25 }

  even_odd_nums = dict(even = [], odd = [] )
  { (even_odd_nums.get("even" if num % 2 == 0 else "odd").append(num)) for num in range(1,10) } #  even_odd_nums -> {'even': [2, 4, 6, 8], 'odd': [1, 3, 5, 7, 9]}
  ```

- Helpful methods - **`clear()` `copy()` `fromkeys()` `get()` `pop()` `update()`**
  ```Python
  artist = { first: "Neil", last: "Young" }

  artist.clear() # {}
  
  artist.copy() # { "first": "Neil", "last": "Young" }
  
  {}.formkeys(["email"], 'unknown') # {'email': 'unknown'}
  
  artist.get('first') # "Neil" or None if the key doesnt exist
  
  artist.pop('first') # "Neil" removes the key, value pair and returns the value

  new_items = { email: "name@server.com"}
  artist.update(new_items) # { email: "name@server.com", first: "Neil", last: "Young" } if the value exists then it overrides it
  ```

### Tuples
An ordered collection or grouping of items. Tuples are immutable. Data in Tuples doesnt have to be unique. We can have nested Tuples.

- To create a tuple
  ```Python
  alphabet = ( "a", "b", "c" )
  ```
  or
  ```Python
  numbers = tuple(1, 2, 3)
  ```

- To get the number of times a value appears in a tuple
  ```Python
  (1,2,3,3,3).count(3) # 3
  ```

- To get the index at which a value is found in a tuple. If its not found, then it returns a **`ValueError`**
  ```Python
  (1,2,3,3,3).index(3) # 2 - only the first matching index is returned
  ```

### Sets
Sets do not have duplicate values. Elements in sets aren't ordered. You cannot access items in a set by index.
  
- To create a set
  ```Python
  numbers = { 1, 4, 5 }
  ```
  or
  ```Python
  numbers = set({1, 4, 5})
  ```

- To check if a value exists in a Set
  ```Python
  4 in { 1, 4, 5 } # True
  ```

- To convert a List to a Set
  ```Python
  set([1, 2, 3, 4, 4, 5, 5]) # {1, 2, 3, 4, 5} Removes all the duplicates
  ```

- To add a element to a Set. If the element is already in the set, the set doesn't change.
  ```Python
  s = set([1, 2, 3])
  s.add(4) # {1, 2, 3, 4}
  ```

- To removes a value from the set. Returns a **`KeyError`** if the value is not found. Need to use **`discard()`** to avoid **`KeyError`** s.
  ```Python
  s = {1,2,3,4,5,6}
  s.remove(3)
  ```

- Sets have quite a few other mathematical methods such as intersection, symmetric_difference, union, etc...
  ```Python
  math_students = { "Matt", "Helen", "Prashant", "James", "Aparna" }
  bio_students = { "Jane", "Matt", "Charlotte", "Mesut", "Oliver", "James" }
  
  # to generate a set with all unique students
  print(math_students | bio_students) # {'Oliver', 'Charlotte', 'James', 'Mesut', 'Helen', 'Matt', 'Jane', 'Prashant', 'Aparna'}

  # to generate a set with students who are in both courses
  print(math_students & bio_students) # {'James', 'Matt'}
  ```

- Helpful methods - **`clear()` `copy()`**
  ```Python
  some_set = {1, 2, 3}.copy() # looks the same, not the same thing in memory

  some_set.clear();
  ```

### Functions and Parameters
- Pass a function as a parameter
  ```Python
  def addition(a,b):
    return a + b

  def calculate(a,b, fn = addition):
    return fn(a,b)

  print(calculate(1,2)) # 3
  ```

- Keyword Arguments
  ```Python
  def full_name(first, last):
    return f"Your full name is {first} {last}."

  print(full_name(first = 'Dilan', last = 'Livera')) # Your full name is Dilan Livera.
  ```

- **`global`** keyword
This is use to manipulate a variable defined in the **`global`** scope. 
  ```Python
  total = 0

  def add_to_total(num):
    global total
    total += num
    print(f"Total = {total}")

  add_to_total(1) # Total = 1
  add_to_total(1) # Total = 2
  ```

- **`nonlocal`** Keyword
Lets us modify a parent's variable in a child function
  ```Python
  def outer():
    count = 0

    def inner():
      nonlocal count
      count += 1

      return count
    
    return inner() 

  print(outer()) # 1
  ```

- Docstrings **`""" """`**
  ```Python
  def exponent(num, power = 2):
    """exponent(num, power) raises num to specified power. Power defaults to 2."""
    return num ** power

  print(exponent(2)) # 4

  print(exponent.__doc__)
  ```

- **`*args`**
A sepcial operator we can pass to a function to gather remaining ***arguments*** as a ***tuple***. **`args`** is just a parameter, we can call it whatever we want.
  ```Python
  def what_is_in_args(*args):
    print(args)

  what_is_in_args(1,2,3,4,5) # (1, 2, 3, 4, 5)
  ```

- **`**kwargs`**
A special operator we can pass to a function to gather remaining ***keyword arguments*** as a ***dictionary***. **`kwargs`** is just a parameter, we can call it whatever we want.
  ```Python
  def what_is_in_kwargs(job, **kwargs):
    print(kwargs)

  what_is_in_kwargs(job = "Software Developer", first_name="Dilan", last_name="Livera") # {'first_name': 'Dilan', 'last_name': 'Livera'}
  ```

- Order of Parameters
  1. parameters
  2. **`*args`**
  3. default parameters
  4. **`**kwargs`**

- ***Tuple*** unpacking
  ```Python
  def sum_of_values(*args):
    total = 0

    for num in args:
      total += num
    
    print(total)

  nums = [1,2,3,4,5]

  sum_of_values(*nums) # 15. nums list is unpacked here.
  ```

- ***Dictionary*** unpacking
  ```Python
  def dictionary_unpacking(first, last):
    print(f"My name is {first} {last}")

  names = dict(first = "Dilan", last = "Livera")

  dictionary_unpacking(**names) # My name is Dilan Livera. names dictionary is unpacked here.
  ```

### Lambdas and Build in Functions
- **`lambda`** s  
lambdas are anonymous functions.
  ```Python
  def calculate(a,b, fn):
    return fn(a, b)

  print(calculate(1,2,lambda x, y: x + y))
  ```

- **`map`**
  ```Python
  nums = [1,2,3,4,5]

  doubles = list(map(lambda x: x * 2, nums)) # doubles = [2, 4, 6, 8, 10]
  ```

### Other
- To check equality of values
  ```Python
  "A" == "B"
  ```

- To check the equality of place in the memory
  ```Python
  clone is d
  ```
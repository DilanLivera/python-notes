# Python Notes

[Python documentation](https://docs.python.org/3/)

### Dictionary
Dictionaries are key value pairs and list are ordered list of elements.

- To create a dictionary
  ```
  cat = { "name": "blue", "age": 3.5 }
  ```
  or
  ```
  cat = dict( name = "blue", age = 3.5 )
  ```

- To Access data from a dictionary
  ```
  cat["name"] # 'blue'
  ```

- To iterate
  ```
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
  ```
  "name" in cat # True
  ```

- To check if value exist in the dictionary
  ```
  "blue" in cat.values() # True
  ```

- Dictionary Comprehension **`{ __:__ for __ in __ }`**
  ```
  numbers = dict( first = 1, second = 2, third = 3)

  { key: value ** 2 for key,value in numbers.items() } # { 'first': 1, 'second': 4, 'third': 9 }

  { num: num**2 for num in [1,2,3,4,5] } # { 1: 1, 2: 4, 3: 9, 4: 16, 5: 25 }

  even_odd_nums = dict(even = [], odd = [] )
  { (even_odd_nums.get("even" if num % 2 == 0 else "odd").append(num)) for num in range(1,10) } #  even_odd_nums -> {'even': [2, 4, 6, 8], 'odd': [1, 3, 5, 7, 9]}
  ```

- Helpful methods - **`clear()` `copy()` `fromkeys()` `get()` `pop()` `update()`**
  ```
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

- To create a dictionary
  ```
  alphabet = ( "a", "b", "c" )
  ```
  or
  ```
  numbers = tuple(1, 2, 3)
  ```

- To get the number of times a value appears in a tuple
  ```
  (1,2,3,3,3).count(3) # 3
  ```

- To get the index at which a value is found in a tuple. If its not found, then it returns a **`ValueError`**
  ```
  (1,2,3,3,3).index(3) # 2 - only the first matching index is returned
  ```

### Sets
Sets do not have duplicate values. Elements in sets aren't ordered. You cannot access items in a set by index.
  
- To create a dictionary
  ```
  numbers = { 1, 4, 5 }
  ```
  or
  ```
  numbers = set({1, 4, 5})
  ```

- To check if a value exists in a Set
  ```
  4 in { 1, 4, 5 } # True
  ```

- To convert a List to a Set
  ```
  set([1, 2, 3, 4, 4, 5, 5]) # {1, 2, 3, 4, 5} Removes all the duplicates
  ```

- To add a element to a Set. If the element is already in the set, the set doesn't change.
  ```
  s = set([1, 2, 3])
  s.add(4) # {1, 2, 3, 4}
  ```

- To removes a value from the set. Returns a **`KeyError`** if the value is not found. Need to use **`discard()`** to avoid **`KeyError`** s.
  ```
  s = {1,2,3,4,5,6}
  s.remove(3)
  ```

- Sets have quite a few other mathematical methods such as intersection, symmetric_difference, union, etc...
  ```
  math_students = { "Matt", "Helen", "Prashant", "James", "Aparna" }
  bio_students = { "Jane", "Matt", "Charlotte", "Mesut", "Oliver", "James" }
  
  # to generate a set with all unique students
  print(math_students | bio_students) # {'Oliver', 'Charlotte', 'James', 'Mesut', 'Helen', 'Matt', 'Jane', 'Prashant', 'Aparna'}

  # to generate a set with students who are in both courses
  print(math_students & bio_students) # {'James', 'Matt'}
  ```

- Helpful methods - **`clear()` `copy()`**
  ```
  some_set = {1, 2, 3}.copy() # looks the same, not the same thing in memory

  some_set.clear();
  ```

### Other
- To check equality of values
  ```
  "A" == "B"
  ```

- To check the equality of place in the memory
  ```
  clone is d
  ```

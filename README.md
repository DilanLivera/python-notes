# Python Notes

[Python 3.8.2 documentation](https://docs.python.org/3/)

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

- Dictionary Comprehension `{ __:__ for __ in __ }`
  ```
  numbers = dict( first = 1, second = 2, third = 3)

  { key: value ** 2 for key,value in numbers.items() } # { 'first': 1, 'second': 4, 'third': 9 }

  { num: num**2 for num in [1,2,3,4,5] } # { 1: 1, 2: 4, 3: 9, 4: 16, 5: 25 }

  even_odd_nums = dict(even = [], odd = [] )
  { (even_odd_nums.get("even" if num % 2 == 0 else "odd").append(num)) for num in range(1,10) } #  even_odd_nums -> {'even': [2, 4, 6, 8], 'odd': [1, 3, 5, 7, 9]}
  ```

- Helpful methods - `clear()` `copy()` `fromkeys()` `get()` `pop()` `update()`
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

### Other
- To check equality of values
  ```
  "A" == "B"
  ```

- To check the equality of place in the memory
  ```
  clone is d
  ```

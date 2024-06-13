---
layout: post
title: Hash Table
category: tech
external-url:
---

Ever wonder why searching in a list is O(N) but in a dictionary is O(1)? I implemented a simple python class to reimplement a `dict` and understand all the *beauty* of this data structure.

The first hint is in the title of the article, a hash table. To understand, we first need to know what is a hash function. From Wikipedia, "A hash function is any function that can be used to map data of arbitrary size to fixed-size values".

One of the utility of hashing is to validate the integrity of a file, a message, or a transaction. For example, if you have a file `secret.md` with a secret message.

```zsh
> echo "I don't like papaya." > secret.md; md5 secret.md
MD5 (secret.md) = d7aa89920e4edaad0ae513e60b6f12a8
```

the md5 (a hashing function) returns the hashed value of all content of the file as a 32-character hexadecimal number (128 bits, `d7aa89920e4edaad0ae513e60b6f12a8`. If we modify the message inside the file, simulating a data loss or tampering.

```zsh
> echo "I like papaya." > secret.md; md5 secret.md
MD5 (secret.md) = 59ebb8853dcd6b4d0d9eca6f26453d79
```
the resulting hash is different. Now back to our data structure.

## Dictionary implementation

A dictionary is a data structure that stores *key-value* pairs. Each value is stored (and accessed) using its key, which is hashed to determine its index in the underlying list.

In Python, there is a `hash` function part of the standard library.
```python
>>> hash(100)
100
>>> hash("hello")
2167104979566369208
>>> hash("Hello")
5232884906401865102
```
We can see that hashes of integers are directly the integers themselves, while strings are hashed to long integers. Important to note that the hash function returns a different value for "hello" and "Hello" to allow the usage of case sensitive keys to access the data.

To map a key to its index, we can take the modulo of the hash with respect to the size of our hash table. Let's say we defined an underlying list to store the data (`self.data`) with 1000 empty elements, the `index_from_key` can be defined as follow:

```python
MAX_SIZE = 1000

class HashTable:
    def __init__(self, max_size=MAX_SIZE):
        self.data = [[] for _ in range(max_size)]

    def index_from_key(self, key):
        return hash(key) % len(self.data)
```
with the `self.data` a list containing 1000 empty lists to store the dictionnary data.

## Collision

If we go back to the md5 hashing function, the probability of the hashed value accidentally  "colliding", i.e two different inputs producing the same hashed value, is 1/2**128. In our case here, with only 1000 indices, the likelihood of colliding is much higher, e.g. `index_from_key(1) == index_from_key(1001)`. To handle collisions, we can store multiple elements as `(key, value)` at the same index in a list, ensuring all entries are retained."

That can be implemented as follow:

```python
    def __setitem__(self, key, value):
        idx = self.index_from_key(key)

        # check if it exists
        for i, (k, v) in enumerate(self.data[idx]):
            if k == key:
                self.data[idx][i] = (key, value)
                return

        # otherwise add to index
        self.data[idx].append((key, value))

    def __getitem__(self, key):
        idx = self.index_from_key(key)
        for k, v in self.data[idx]:
            if k == key:
                return v
        raise KeyError(f"Key {key} not found")
```
and looping the retrieved values and comparing if the current key matches (`if k == key:`). If we have a handful of keys to compare, it is still much faster than having to look all the elements of a the list, hence can be considered O(1).

## Optimization

While this is a very simple implementation, dictionaries are a fundamental and highly efficient data structure in Python, used extensively throughout the language. The complete implementation in CPython is significantly more complex 🥵 than the 50 lines of code below. For those interested, you can explore the complete source code ([cpython/Objects
/dictobject.c](https://github.com/python/cpython/blob/main/Objects/dictobject.c)).

## Code

Complete code and some tests.

```python
MAX_SIZE = 1000

class HashTable:
    def __init__(self, max_size=MAX_SIZE):
        self.data = [[] for _ in range(max_size)]

    def index_from_key(self, key):
        return hash(key) % len(self.data)

    def __getitem__(self, key):
        idx = self.index_from_key(key)
        for k, v in self.data[idx]:
            if k == key:
                return v
        raise KeyError(f"Key {key} not found")

    def __setitem__(self, key, value):
        idx = self.index_from_key(key)

        # check if it exists
        for i, (k, v) in enumerate(self.data[idx]):
            if k == key:
                self.data[idx][i] = (key, value)
                return

        # otherwise add to index
        self.data[idx].append((key, value))

    def __iter__(self):
        for bucket in self.data:
            if bucket:
                for k, v in bucket:
                    yield k, v

    def __len__(self):
        return sum(len(bucket) for bucket in self.data)

    def repr_item(self, value):
        return f"'{value}'" if isinstance(value, str) else value

    def __repr__(self):
        text = []
        for bucket in self.data:
            if bucket:
                for k, v in bucket:
                    text.append(f"{self.repr_item(k)}: {self.repr_item(v)}")
        return "{" + ", ".join(text) + "}"

    def __str__(self):
        return repr(self)

# set values
table = HashTable()
table["🚀"] = 1
table["b"] = "linux"
table[10] = (4, 9)

# assert set
assert table["🚀"] == 1
assert table["b"] == "linux"
assert table[10] == (4, 9)

# assert modify
table[10] = 0
assert table[10] == 0

# print hash table
print(table)

# should raise KeyError
table[123]
```
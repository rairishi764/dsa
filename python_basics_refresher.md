# Python Basics Refresher — A Tutor's Guide

> A focused syntax + concepts refresher for someone with basic Python who is heading
> into DSA / interview prep. Read top-to-bottom once, then use it as a lookup sheet.

**How to use this doc:** Each section has (1) the *minimum* syntax you must remember,
(2) a "gotcha" callout for the things that trip people up in interviews, and (3) a
short pointer to a free, open-source book where you can dig deeper.

---

## Table of Contents

1. [Variables & Initialization](#1-variables--initialization)
2. [Built-in Data Types at a Glance](#2-built-in-data-types-at-a-glance)
3. [Loops — `for`, `while`, comprehensions](#3-loops)
4. [Classes, `self`, and "Public/Private"](#4-classes-self-and-publicprivate)
5. [List vs Array — the distinction that matters](#5-list-vs-array--the-distinction-that-matters)
6. [Dict vs Map vs Set — when to use what](#6-dict-vs-map-vs-set)
7. [Quick Cheatsheet](#7-quick-cheatsheet)
8. [Recommended Open-Source Books](#8-recommended-open-source-books)

---

## 1. Variables & Initialization

Python variables are **names bound to objects**. There is no "declaration" — assignment
*is* the declaration. The type lives on the object, not the name.

```python
# Basic assignment
name      = "Rishi"          # str
age       = 31               # int
pi        = 3.14159          # float
is_ready  = True             # bool
nothing   = None             # NoneType (Python's "null")
```

### Multiple assignment / unpacking

```python
x, y, z = 1, 2, 3            # tuple unpacking
a = b = c = 0                # chained — all three point to the SAME object
first, *rest = [1, 2, 3, 4]  # first=1, rest=[2,3,4]   <- common in DSA
```

### Type hints (optional but interview-friendly)

```python
count: int = 0
names: list[str] = []
lookup: dict[str, int] = {}
```

Type hints don't change runtime behavior — they're documentation the interpreter
ignores but `mypy` / IDEs use to catch bugs.

### Constants

Python has no real constants. Convention: **`UPPER_SNAKE_CASE`** signals "don't reassign me".

```python
MAX_RETRIES = 3
PI = 3.14159
```

### Gotcha — mutable default arguments

```python
def bad(items=[]):           # DON'T — the [] is shared across calls
    items.append(1)
    return items

def good(items=None):        # DO
    if items is None:
        items = []
    items.append(1)
    return items
```

> **Book pointer:** *Think Python* (Allen Downey), Ch. 2 "Variables, Expressions and Statements" — the cleanest explanation of names-vs-values you'll find.

---

## 2. Built-in Data Types at a Glance

| Category   | Type     | Mutable? | Example                       | DSA usage             |
|------------|----------|----------|-------------------------------|-----------------------|
| Numeric    | `int`    | no       | `42`                          | counters, indices     |
| Numeric    | `float`  | no       | `3.14`                        | weighted graphs       |
| Text       | `str`    | **no**   | `"hello"`                     | string problems       |
| Sequence   | `list`   | yes      | `[1, 2, 3]`                   | the workhorse         |
| Sequence   | `tuple`  | no       | `(1, 2)`                      | hashable, multi-return|
| Mapping    | `dict`   | yes      | `{"a": 1}`                    | hashmap problems      |
| Set        | `set`    | yes      | `{1, 2, 3}`                   | dedup, O(1) lookup    |
| Set        | `frozenset` | no    | `frozenset([1,2])`            | hashable set          |
| Boolean    | `bool`   | no       | `True` / `False`              | flags                 |
| None       | `NoneType` | no     | `None`                        | absence of value      |

**Mutable** means you can change the object in place (`list.append`). **Immutable** means
any "change" creates a new object (`s = s + "x"` makes a new string).

This matters in interviews because:
- Immutable objects are **hashable** → they can be `dict` keys / `set` members.
- Mutable objects passed to functions can be modified by the callee (a common bug source).

---

## 3. Loops

### `for` loop — iterate over any iterable

```python
nums = [10, 20, 30]

for n in nums:               # over values
    print(n)

for i in range(len(nums)):   # over indices
    print(i, nums[i])

for i, n in enumerate(nums): # idiomatic: index + value
    print(i, n)

for a, b in zip([1,2,3], ['x','y','z']):   # parallel iteration
    print(a, b)
```

### `while` loop

```python
i = 0
while i < 5:
    print(i)
    i += 1
```

Use `while` when the **stop condition** matters more than the count — e.g. binary search,
two-pointer problems, "process until queue is empty".

### `break`, `continue`, `else`

```python
for n in nums:
    if n < 0:
        continue             # skip this iteration
    if n > 100:
        break                # exit the loop entirely
else:
    # runs ONLY if the loop finished without `break`
    print("no value > 100 found")
```

The `for...else` construct is unusual but shows up in search problems — remember it.

### Comprehensions (Pythonic loops)

```python
squares  = [x*x for x in range(10)]                  # list comp
evens    = [x for x in range(20) if x % 2 == 0]      # with filter
matrix   = [[0]*3 for _ in range(3)]                 # 3x3 grid (do NOT use [[0]*3]*3)
lookup   = {x: x*x for x in range(5)}                # dict comp
unique   = {x % 3 for x in range(10)}                # set comp
gen      = (x*x for x in range(10))                  # generator (lazy, memory-cheap)
```

### Gotcha — the `[[0]*3]*3` trap

```python
grid = [[0]*3]*3             # WRONG — all 3 rows are the SAME list
grid[0][0] = 9               # mutates row 0... and 1, and 2
# grid is now [[9,0,0], [9,0,0], [9,0,0]]

grid = [[0]*3 for _ in range(3)]   # CORRECT — three independent lists
```

> **Book pointer:** *Automate the Boring Stuff with Python* (Al Sweigart), Ch. 2 "Flow Control" + Ch. 4 "Lists" — beginner-friendly tour of every loop pattern.

---

## 4. Classes, `self`, and "Public/Private"

### Minimal class

```python
class Stack:
    def __init__(self, capacity=10):     # constructor
        self.capacity = capacity         # instance attribute
        self._items = []                 # "protected" by convention

    def push(self, x):
        self._items.append(x)

    def pop(self):
        return self._items.pop()

    def __len__(self):                   # dunder — enables len(stack)
        return len(self._items)

    def __repr__(self):                  # how it prints in REPL/debugging
        return f"Stack({self._items})"

s = Stack()
s.push(1); s.push(2)
print(len(s))   # 2
```

- `__init__` is the constructor.
- `self` is the explicit receiver (Python doesn't have implicit `this`).
- "Dunder" methods (`__len__`, `__eq__`, `__lt__`, `__repr__`, `__iter__`) make your
  class plug into built-ins like `len()`, `==`, `sorted()`, `for x in obj`, `print()`.

### Class vs instance attributes

```python
class Counter:
    total_created = 0            # class attribute — shared across instances

    def __init__(self):
        self.value = 0           # instance attribute — per object
        Counter.total_created += 1
```

### Public / Private — convention, not enforcement

Python has **no real private**. It uses naming conventions:

| Name       | Meaning                                                |
|------------|--------------------------------------------------------|
| `name`     | **Public** — part of the API.                          |
| `_name`    | **Protected (by convention)** — "internal, don't touch". Linters warn. |
| `__name`   | **Name-mangled** — Python rewrites it to `_ClassName__name` to avoid subclass collisions. NOT security. |
| `name_`    | Trailing underscore avoids clashing with keywords (`class_`, `id_`). |

```python
class BankAccount:
    def __init__(self, balance):
        self.owner    = "Rishi"      # public
        self._balance = balance      # protected — please use the methods
        self.__pin    = "1234"       # name-mangled to _BankAccount__pin

    def deposit(self, amount):
        self._balance += amount

acc = BankAccount(100)
print(acc._balance)              # works, but you're "breaking the contract"
# print(acc.__pin)               # AttributeError
print(acc._BankAccount__pin)     # works — proves __ is not security
```

**Key mindset:** "We're all consenting adults here." Python trusts you to respect the
underscore convention rather than enforcing it.

### Properties (the Pythonic getter/setter)

```python
class Temperature:
    def __init__(self, celsius):
        self._c = celsius

    @property
    def fahrenheit(self):                  # acts like an attribute
        return self._c * 9/5 + 32

    @fahrenheit.setter
    def fahrenheit(self, value):
        self._c = (value - 32) * 5/9

t = Temperature(0)
print(t.fahrenheit)      # 32.0  (no parens — looks like an attribute)
t.fahrenheit = 212
print(t._c)              # 100.0
```

Use `@property` instead of writing Java-style `get_x()` / `set_x()` methods.

### Inheritance, very briefly

```python
class Animal:
    def speak(self):
        return "..."

class Dog(Animal):
    def speak(self):
        return "Woof"

Dog().speak()    # 'Woof'
```

Use `super().__init__(...)` in `__init__` to call the parent's constructor.

> **Book pointer:** *Composing Programs* (John DeNero, UC Berkeley CS61A) — Ch. 2.5 "Object-Oriented Programming". The clearest treatment of why Python's "consenting adults" model differs from Java/C++.

---

## 5. List vs Array — the distinction that matters

This trips up people coming from Java/C++. Python has **three** things that look like arrays:

### 5a. `list` — what you almost always want

```python
nums = [1, 2, 3]
nums.append(4)           # O(1) amortized
nums.insert(0, 0)        # O(n) — shifts everything
nums.pop()               # O(1) from end
nums.pop(0)              # O(n) from front  ← use deque instead
nums[1:3]                # slicing → new list
len(nums)                # O(1)
```

- A `list` is a **dynamic, heterogeneous** sequence backed by a resizable array of
  **pointers to objects**. Elements can be of mixed types.
- Random access is `O(1)`. Append is amortized `O(1)`. Insert/delete in the middle is `O(n)`.

### 5b. `array.array` — typed, compact, rarely used

```python
from array import array
ints = array('i', [1, 2, 3])        # 'i' = signed int
ints.append(4)
```

- Same API as `list` but **all elements must be the same C type**.
- Memory-efficient (no per-element pointer overhead) but you almost never need it
  unless you're squeezing memory in a numeric workload.
- For real numerical work, use **NumPy** (`np.array`) instead.

### 5c. `numpy.ndarray` — the real "array" of Python

```python
import numpy as np
a = np.array([1, 2, 3])
a * 2                    # → array([2, 4, 6])    vectorized, fast
a.shape                  # (3,)
```

- Fixed-type, fixed-shape, contiguous memory.
- Vectorized operations are **way** faster than Python loops.
- This is what scientific Python / ML code means by "array".

### When to use what — interview rule of thumb

| Need                                          | Reach for          |
|-----------------------------------------------|--------------------|
| General-purpose sequence, mixed types         | `list`             |
| Stack (LIFO)                                  | `list` (`append`/`pop`) |
| Queue / deque (FIFO, both ends)               | `collections.deque` |
| Heavy numeric work, vectorized math           | `numpy.ndarray`    |
| Memory-efficient typed buffer (rare)          | `array.array`      |

### The big mental model

> A Python `list` is a **dynamic array of references**, not a true array of contiguous
> values. That's why it's flexible (any types) but slower than a NumPy array for math.

> **Book pointer:** *Problem Solving with Algorithms and Data Structures using Python*
> (Miller & Ranum, free at runestone.academy), Ch. 2 "Analysis" + Ch. 3 "Basic Data
> Structures" — covers Big-O of every list operation. **Highly recommended for DSA prep.**

---

## 6. Dict vs Map vs Set

### "Map" in Python = `dict`

Python doesn't have a type called `map`. The data structure other languages call a
"map" / "hashmap" / "associative array" is Python's **`dict`**. (Confusingly, Python
*does* have a `map()` *function*, which is unrelated — it applies a function to an
iterable.)

```python
ages = {"alice": 30, "bob": 25}      # dict literal
ages["carol"] = 27                   # insert
ages["alice"]                        # lookup — O(1) average
"bob" in ages                        # membership test — O(1) average
del ages["bob"]
ages.get("zach", 0)                  # safe lookup with default

for key in ages:                     # iterate keys
    ...
for key, val in ages.items():        # iterate pairs ← idiomatic
    ...
```

**Implementation:** Hash table. Average `O(1)` for insert/lookup/delete. Since Python 3.7,
**dicts preserve insertion order** — that's a language guarantee, not an implementation detail.

### Useful dict variants

```python
from collections import defaultdict, Counter, OrderedDict

# defaultdict — auto-creates a value when a missing key is accessed
groups = defaultdict(list)
groups["fruits"].append("apple")     # no KeyError, creates [] automatically

# Counter — frequency map, hugely useful in DSA string problems
freq = Counter("mississippi")
# Counter({'i': 4, 's': 4, 'p': 2, 'm': 1})
freq.most_common(2)                  # [('i', 4), ('s', 4)]
```

### `set` — unordered collection of unique, hashable values

```python
seen = set()
seen.add(5)
5 in seen                            # O(1)
{1,2,3} | {3,4}                      # union  → {1,2,3,4}
{1,2,3} & {2,3,4}                    # intersection → {2,3}
{1,2,3} - {2}                        # difference → {1,3}
```

### Choosing between them — interview decision tree

| Question                                                         | Use      |
|------------------------------------------------------------------|----------|
| "Have I seen this value before?" (dedup, fast membership)        | `set`    |
| "What is associated with this key?" (key → value lookup)         | `dict`   |
| "How many times does each thing appear?"                         | `Counter`|
| "Group items by some property"                                   | `defaultdict(list)` |
| "I need order preserved + key lookup"                            | `dict` (insertion order is preserved) |

### Critical rule — keys must be hashable

```python
d = {}
d[(1, 2)] = "ok"           # tuple of ints — hashable, fine
d[[1, 2]] = "boom"         # TypeError: unhashable type: 'list'
```

Hashable ≈ immutable. Strings, numbers, tuples (of hashables), and frozensets are
hashable. Lists, dicts, and sets are not.

### Why this matters for DSA

About **40% of LeetCode "easy" + "medium" array/string problems** are solved by reaching
for a `dict` or `set` to get `O(1)` lookups and trade space for time. Examples:

- *Two Sum* → dict mapping value → index
- *Group Anagrams* → defaultdict keyed by sorted-letters
- *Longest Substring Without Repeating Characters* → set + sliding window
- *Top K Frequent Elements* → `Counter`
- *Contains Duplicate* → `set`

> **Book pointer:** *Python for Everybody* (Charles Severance, py4e.com), Ch. 9 "Dictionaries"
> + Ch. 10 "Tuples" — gentlest possible introduction with great visuals on hash lookups.

---

## 7. Quick Cheatsheet

```python
# --- creation ---
x = 0; xs = []; d = {}; s = set(); t = ()

# --- list essentials ---
xs.append(1)              # add to end       O(1)
xs.pop()                  # remove from end  O(1)
xs.pop(0)                 # remove from front O(n)  — prefer deque
xs.insert(0, 9)           # insert at front  O(n)
xs.sort()                 # in-place         O(n log n)
sorted(xs, reverse=True)  # returns new list
xs[::-1]                  # reversed copy
xs[1:4]                   # slice  [start:stop)
xs[::2]                   # every 2nd element

# --- dict essentials ---
d[k] = v
v = d.get(k, default)
for k, v in d.items(): ...
d.setdefault(k, []).append(x)

# --- set essentials ---
s.add(x); s.discard(x); x in s

# --- string essentials (strings are immutable!) ---
"hello".upper(); "hello".split(",")
",".join(["a","b","c"])     # 'a,b,c'
"abc"[::-1]                  # 'cba'
s.startswith("he"); s.find("ll")

# --- common helpers ---
len(x); sum(xs); min(xs); max(xs)
any(xs); all(xs)
zip(a, b); enumerate(xs); range(0, 10, 2)

# --- collections module — DSA staples ---
from collections import deque, Counter, defaultdict
dq = deque()
dq.append(x); dq.appendleft(x)
dq.pop();     dq.popleft()       # both O(1)
```

---

## 8. Recommended Open-Source Books

All of these are **free** and **legally available** under open licenses (Creative
Commons or similar). Bookmark two or three and revisit as you progress through your
DSA plan.

| # | Book | Author | Why it's worth your time | Link |
|---|------|--------|--------------------------|------|
| 1 | **Think Python (2e)** | Allen B. Downey | The most rigorous, computer-sciency intro. Best for building a clean mental model of names, objects, and references. | greenteapress.com/wp/think-python-2e |
| 2 | **Automate the Boring Stuff with Python** | Al Sweigart | Practical, friendly, project-driven. Great for cementing syntax through small useful scripts. | automatetheboringstuff.com |
| 3 | **Python for Everybody (Py4E)** | Charles Severance | Gentlest on-ramp; pairs with a free Coursera course. Excellent dict / file / web chapters. | py4e.com/book |
| 4 | **A Byte of Python** | Swaroop C H | Compact (~100 pages) refresher — exactly the "I forgot the syntax" book. | python.swaroopch.com |
| 5 | **Composing Programs** | John DeNero (UC Berkeley CS61A) | The OOP and higher-order-function chapters are *the* best free explanation of these topics. | composingprograms.com |
| 6 | **Problem Solving with Algorithms and Data Structures using Python** | Miller & Ranum | **The single most relevant book for your DSA prep.** Covers Big-O, lists, stacks, queues, trees, graphs, and more, all in Python. | runestone.academy/ns/books/published/pythonds/index.html |
| 7 | **The Hitchhiker's Guide to Python** | Kenneth Reitz et al. | Community-maintained guide on idiomatic Python, project layout, and tooling. Read once you're comfortable with the basics. | docs.python-guide.org |
| 8 | **Dive Into Python 3** | Mark Pilgrim | Older but still excellent for understanding Python idioms in depth. | diveintopython3.problemsolving.io |

### Suggested reading order for *your* DSA journey

1. **Now (refresher week):** This document + skim *A Byte of Python*.
2. **Weeks 1–3 (arrays, strings, hashmaps, linked lists, stacks, queues):**
   *Problem Solving with Algorithms and Data Structures using Python*, Chapters 2–4.
3. **Weeks 4–6 (recursion, trees, graphs):** Same book, Chapters 5–7.
4. **Anytime you're stuck on an OOP concept:** *Composing Programs*, Chapter 2.
5. **Weekend evenings, low-energy reading:** *Think Python* — short chapters, builds intuition.

---

## Final advice from your "tutor"

1. **Type the examples, don't just read them.** Use the Jupyter notebook
   `python_dsa_crash_course.ipynb` already in this folder as a scratchpad.
2. **Whenever you write a `list`, ask: do I actually need a `set` or `dict`?** This single
   habit will fix 80% of "my solution times out" issues on LeetCode.
3. **Memorize the Big-O of each `list`/`dict`/`set` operation.** Section 7 is your
   cheatsheet — drill it until it's reflex.
4. **Every dunder method you learn is a power-up.** `__len__`, `__iter__`, `__lt__`, and
   `__eq__` will let your classes work seamlessly with `len()`, `for`, `sorted()`, and `in`.

Good luck — and refer back to this doc whenever Python syntax slips. 

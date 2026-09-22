# What Is a Dictionary?

A **dictionary** stores pairs of **key → value**. Each key is unique and points to exactly one value. You read and write values using the key — not a position.

Compare it with a list:

* **`List<string>`** — values in order, accessed by index: **`names[0]`**, **`names[1]`** …
* **`Dictionary<string, int>`** — values accessed by a key that you choose yourself: **`ages["Ada"]`**, **`ages["Alan"]`** …

The type is written as **`Dictionary<TKey, TValue>`** — first the key type, then the value type. **`Dictionary<string, int>`** means “keys are strings, values are integers.”

---

## When Do You Use a Dictionary?

Use a dictionary when you want to **look something up quickly using an identifier** instead of searching through a list:

* Age by name: **`"Ada" → 36`**
* Price by product number: **`"A-101" → 249`**
* Occurrence counts: count how many times each word appears in a text (**`"and" → 12`**)
* Settings: **`"language" → "en"`**

Rule of thumb: **if each item has a natural “key”** (a name, an ID, a word) that you want to use to find a value, a dictionary is a good fit. If you only need to keep a sequence of values in order, a list is usually enough.

---

## Syntax

### Create

```csharp
using System.Collections.Generic;   // usually already included in .NET 10

// Empty dictionary: string keys, int values
Dictionary<string, int> ages = new();

// With values from the start
Dictionary<string, int> prices = new()
{
    ["A-101"] = 249,
    ["B-202"] = 99,
};
```

### Add and Update Values

```csharp
ages["Ada"] = 36;    // adds a new key
ages["Alan"] = 41;
ages["Ada"] = 37;    // key already exists -> updates the value
```

Assigning a value using **`ages["Ada"]`** adds the key if it does not already exist, and **overwrites** the value if the key is already present. (There is also **`ages.Add("Ada", 36)`**, but it **throws an exception** if the key already exists — **`["..."] =`** is usually the most convenient approach.)

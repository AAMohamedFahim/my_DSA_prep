# HashMap in Java

A comprehensive guide to using `HashMap` in Java. This document covers everything from `HashMap` fundamentals to Java's key methods, internal working, and performance considerations.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [What is a HashMap?](#what-is-a-hashmap)
4. [How HashMap Works Internally](#how-hashmap-works-internally)
5. [Creating a HashMap](#creating-a-hashmap)
6. [Adding, Retrieving & Removing Elements](#adding-retrieving--removing-elements)
7. [Common Methods Overview](#common-methods-overview)
8. [Iteration Techniques](#iteration-techniques)
9. [Collision Handling](#collision-handling)
10. [Performance Considerations](#performance-considerations)
11. [Common Use-Cases](#common-use-cases)
12. [Full Example](#full-example)

---

## Introduction

A `HashMap` is part of Java's `java.util` package. It implements the `Map` interface and stores data in key-value pairs. It allows fast retrieval, insertion, and deletion based on the key.

**Key Features:**

* Allows `null` keys and multiple `null` values
* No ordering (not sorted, not insertion order)
* Uses hash function for efficient storage and retrieval

---

## Prerequisites

* Java Development Kit (JDK) 8 or later
* Basic knowledge of Java Collections and Generics

---

## What is a HashMap?

A `HashMap` is a data structure that maps keys to values. It is an implementation of a **hash table**.

**Characteristics:**

* Unique keys (duplicate keys overwrite existing values)
* Allows one `null` key
* Allows multiple `null` values

Real-life examples:

* Student ID → Student Name
* Country Code → Country Name
* Product ID → Product Details

---

## How HashMap Works Internally

1. **Hashing:** Uses key's `hashCode()` to compute bucket index
2. **Buckets:** Internally uses an array of buckets
3. **Collision Handling:** Uses Linked List or Red-Black Tree (for high collisions)
4. **Load Factor:** Controls resizing (default 0.75)
5. **Rehashing:** Automatically resizes when capacity threshold is crossed

---

## Creating a HashMap

```java
import java.util.HashMap;

HashMap<Integer, String> map = new HashMap<>();
```

With initial capacity and load factor:

```java
HashMap<Integer, String> map = new HashMap<>(16, 0.75f);
```

---

## Adding, Retrieving & Removing Elements

```java
// Adding key-value pairs
map.put(1, "Apple");
map.put(2, "Banana");
map.put(3, "Cherry");

// Retrieving values
String value = map.get(2); // "Banana"

// Removing an entry
map.remove(3);

// Checking key existence
boolean exists = map.containsKey(1);

// Checking value existence
boolean valueExists = map.containsValue("Apple");
```

---

## Common Methods Overview

| Method                        | Description                       |
| ----------------------------- | --------------------------------- |
| `put(K key, V value)`         | Inserts or updates key-value pair |
| `get(Object key)`             | Retrieves value for given key     |
| `remove(Object key)`          | Removes key-value pair            |
| `containsKey(Object key)`     | Checks if key exists              |
| `containsValue(Object value)` | Checks if value exists            |
| `keySet()`                    | Returns set of all keys           |
| `values()`                    | Returns collection of all values  |
| `entrySet()`                  | Returns set of key-value pairs    |
| `size()`                      | Returns number of entries         |
| `clear()`                     | Removes all mappings              |

---

## Iteration Techniques

1. **Using keySet():**

```java
for (Integer key : map.keySet()) {
    System.out.println(key + " -> " + map.get(key));
}
```

2. **Using entrySet():**

```java
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

3. **Using Iterator:**

```java
Iterator<Map.Entry<Integer, String>> iterator = map.entrySet().iterator();
while (iterator.hasNext()) {
    Map.Entry<Integer, String> entry = iterator.next();
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

---

## Collision Handling

* **Separate Chaining:** Multiple entries stored in the same bucket using Linked List (Java 7 and earlier)
* **Treeification:** Converts bucket to Red-Black Tree if entries exceed threshold (Java 8+)

---

## Performance Considerations

| Operation | Average Time Complexity |
| --------- | ----------------------- |
| get()     | O(1)                    |
| put()     | O(1)                    |
| remove()  | O(1)                    |
| Iteration | O(n)                    |

**Note:**

* Worst case for `get()` and `put()` → O(n) if too many hash collisions (reduced in Java 8 by treeification)
* Resize operation (rehashing) has a high time cost but happens infrequently

---

## Common Use-Cases

* **Caching mechanisms**
* **Database indexing**
* **Counting frequency of elements**
* **Maintaining key-value configurations**

---

## Full Example

```java
import java.util.HashMap;
import java.util.Map;

public class HashMapDemo {
    public static void main(String[] args) {
        HashMap<Integer, String> map = new HashMap<>();

        map.put(1, "Apple");
        map.put(2, "Banana");
        map.put(3, "Cherry");

        System.out.println("Map Contents:");
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println(entry.getKey() + " -> " + entry.getValue());
        }

        map.remove(2);
        System.out.println("\nAfter removing key 2:");
        for (Integer key : map.keySet()) {
            System.out.println(key + " -> " + map.get(key));
        }
    }
}
```

---

# HashMap in Java

A comprehensive guide to using `HashMap` in Java. This document covers everything from `HashMap` fundamentals to Java's key methods, internal working, and performance considerations. It also dives deep into advanced operations such as counting element frequencies, default values, merging, and more.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [What is a HashMap?](#what-is-a-hashmap)
4. [How HashMap Works Internally](#how-hashmap-works-internally)
5. [Creating a HashMap](#creating-a-hashmap)
6. [Basic HashMap Operations](#basic-hashmap-operations)
7. [Advanced Operations](#advanced-operations)

   * [Counting Element Frequencies](#counting-element-frequencies)
   * [getOrDefault()](#getordefault)
   * [putIfAbsent()](#putifabsent)
   * [merge()](#merge)
   * [compute() / computeIfAbsent() / computeIfPresent()](#compute)
   * [replace()](#replace)
   * [clear() / isEmpty() / size()](#clear-isempty-size)
8. [Adding, Retrieving & Removing Elements](#adding-retrieving--removing-elements)
9. [Iteration Techniques](#iteration-techniques)
10. [Collision Handling](#collision-handling)
11. [Performance Considerations](#performance-considerations)
12. [Common Use-Cases](#common-use-cases)
13. [Full Example](#full-example)

---

## Introduction

A `HashMap` is part of Java's `java.util` package. It implements the `Map` interface and stores data in key-value pairs. It allows fast retrieval, insertion, and deletion based on the key.

**Key Features:**

* Allows one `null` key and multiple `null` values
* No ordering (not sorted, not insertion order)
* Uses hash function for efficient storage and retrieval

---

## Prerequisites

* Java Development Kit (JDK) 8 or later
* Basic knowledge of Java Collections and Generics

---

## What is a HashMap?

A `HashMap` is a data structure that maps unique keys to values. It is Java’s implementation of a **hash table**.

**Characteristics:**

* Unique keys (duplicate keys overwrite existing values)
* Allows one `null` key
* Allows multiple `null` values

**Real-life examples:**

* Student ID → Student Name
* Country Code → Country Name
* Product ID → Product Details

---

## How HashMap Works Internally

1. **Hashing:** Computes `hashCode()` of key and applies supplemental hashing
2. **Buckets:** Uses an array of buckets indexed by hash
3. **Collision Handling:** Separate Chaining (Linked List) or Treeification (Red-Black Tree in Java 8+)
4. **Load Factor:** Defaults to `0.75`. When size exceeds `capacity * loadFactor`, map resizes (doubling capacity).
5. **Rehashing:** All existing entries are redistributed into new buckets after resize.

---

## Creating a HashMap

```java
import java.util.HashMap;

// Default initial capacity = 16, load factor = 0.75
HashMap<Integer, String> map = new HashMap<>();

// Custom initial capacity and load factor
HashMap<Integer, String> customMap = new HashMap<>(32, 0.5f);
```

---

## Basic HashMap Operations

| Operation       | Method                        | Description                         | Time Complexity |
| --------------- | ----------------------------- | ----------------------------------- | --------------- |
| Insert / Update | `put(K key, V value)`         | Inserts or updates a key-value pair | O(1)            |
| Retrieve        | `get(Object key)`             | Retrieves the value for a given key | O(1)            |
| Remove          | `remove(Object key)`          | Deletes a key-value pair            | O(1)            |
| Contains Key    | `containsKey(Object key)`     | Checks if key exists                | O(1)            |
| Contains Value  | `containsValue(Object value)` | Checks if value exists              | O(n)            |
| Size            | `size()`                      | Returns number of key-value pairs   | O(1)            |
| Clear           | `clear()`                     | Removes all key-value pairs         | O(n)            |
| Is Empty        | `isEmpty()`                   | Checks if map is empty              | O(1)            |

---

## Advanced Operations

### Counting Element Frequencies

Use a `HashMap` to count occurrences (frequency) of each element in a collection.

```java
List<String> words = Arrays.asList("apple", "banana", "apple", "orange", "banana", "apple");
Map<String, Integer> freq = new HashMap<>();
for (String w : words) {
    freq.put(w, freq.getOrDefault(w, 0) + 1);
}
System.out.println("Frequencies: " + freq);
// Output: {orange=1, banana=2, apple=3}
```

### getOrDefault()

Retrieves value by key or returns a default if the key is absent.

```java
int count = freq.getOrDefault("pear", 0);
```

### putIfAbsent()

Inserts the key-value pair only if the key is not already present.

```java
map.putIfAbsent(4, "Date");
```

### merge()

Merges a value for a key using a remapping function.

```java
// Add one more "banana" to freq
freq.merge("banana", 1, Integer::sum);
// Now banana count becomes 3
```

### compute(), computeIfAbsent(), computeIfPresent()

Compute a mapping for a key

```java
// Double the count for "apple" if present
freq.computeIfPresent("apple", (k, v) -> v * 2);
```

### replace()

Replaces the value for a key if it is present.

```java
map.replace(1, "Apricot");
```

### clear() / isEmpty() / size()

```java
map.clear();
boolean empty = map.isEmpty();
int total = map.size();
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

// Counting elements
int total = map.size();
```

---

## Iteration Techniques

1. **Using keySet():**

```java
for (K key : map.keySet()) {
    System.out.println(key + " -> " + map.get(key));
}
```

2. **Using entrySet():**

```java
for (Map.Entry<K, V> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

3. **Using Iterator:**

```java
Iterator<Map.Entry<K, V>> it = map.entrySet().iterator();
while (it.hasNext()) {
    Map.Entry<K, V> entry = it.next();
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

---

## Collision Handling

* **Separate Chaining:** Stores multiple entries in the same bucket via linked list (Java 7 and earlier)
* **Treeification:** Converts bucket list to Red-Black Tree when entries exceed threshold (Java 8+)

---

## Performance Considerations

| Operation | Average Time Complexity | Worst Case             |
| --------- | ----------------------- | ---------------------- |
| get()     | O(1)                    | O(n) (hash collisions) |
| put()     | O(1)                    | O(n)                   |
| remove()  | O(1)                    | O(n)                   |
| Iteration | O(n)                    | O(n)                   |

**Notes:**

* High collision rate can degrade performance.
* Resizing (rehashing) is expensive but occurs infrequently.

---

## Common Use-Cases

* **Caching mechanisms**
* **Database indexing**
* **Counting frequency of elements**
* **Maintaining key-value configurations**

---

## Full Example

```java
import java.util.*;

public class HashMapDemo {
    public static void main(String[] args) {
        Map<Integer, String> map = new HashMap<>();

        // Basic puts
        map.put(1, "Apple");
        map.put(2, "Banana");
        map.put(3, "Cherry");

        // Print map
        System.out.println("Map Contents:");
        map.forEach((k, v) -> System.out.println(k + " -> " + v));

        // Counting frequencies
        List<String> list = Arrays.asList("apple", "banana", "apple", "orange", "banana");
        Map<String, Integer> freq = new HashMap<>();
        list.forEach(w -> freq.put(w, freq.getOrDefault(w, 0) + 1));
        System.out.println("\nFrequencies: " + freq);

        // Advanced operations
        freq.merge("banana", 1, Integer::sum);
        freq.computeIfPresent("apple", (k, v) -> v * 2);
        System.out.println("\nAfter modifications: " + freq);

        // Removal and size
        freq.remove("orange");
        System.out.println("\nAfter removing 'orange': " + freq);
        System.out.println("Total elements in freq map: " + freq.size());
    }
}
```

---

*This README provides a one-stop guide for anyone looking to master `HashMap` in Java—from fundamentals to advanced usage.*

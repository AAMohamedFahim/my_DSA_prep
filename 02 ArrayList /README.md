# ArrayList in Java

A comprehensive guide to using `ArrayList` in Java. This document covers everything you need to know, from basic creation to advanced operations and performance considerations.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Creating an ArrayList](#creating-an-arraylist)
4. [Adding Elements](#adding-elements)
5. [Accessing Elements](#accessing-elements)
6. [Updating Elements](#updating-elements)
7. [Removing Elements](#removing-elements)
8. [Iterating over an ArrayList](#iterating-over-an-arraylist)
9. [Other Common Methods](#other-common-methods)
10. [Capacity and Performance](#capacity-and-performance)
11. [Converting Between ArrayList and Array](#converting-between-arraylist-and-array)
12. [Thread Safety and Synchronization](#thread-safety-and-synchronization)
13. [Best Practices and Tips](#best-practices-and-tips)
14. [Full Example](#full-example)

---

## Introduction

`ArrayList` is a part of Java's **Collections Framework**. It provides a resizable array-like data structure that can grow or shrink dynamically as elements are added or removed. It is a generic class, allowing you to specify the type of elements it holds.

Key characteristics:

* **Dynamic Size**: Automatically resizes itself when elements are added or removed.
* **Ordered**: Maintains insertion order of elements.
* **Allows Duplicates**: Can contain multiple occurrences of the same element.
* **Not Synchronized**: Not thread-safe by default.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later.
* Basic knowledge of Java syntax and collections.

---

## Creating an ArrayList

```java
import java.util.ArrayList;

// Create an empty ArrayList of Strings
ArrayList<String> list = new ArrayList<>();

// Create with initial capacity
ArrayList<Integer> numbers = new ArrayList<>(20);

// Create from another collection
List<String> other = List.of("A", "B");
ArrayList<String> copy = new ArrayList<>(other);
```

---

## Adding Elements

```java
list.add("Alice");         // add at end
list.add(0, "Bob");        // insert at index 0

// Add all elements from another collection
list.addAll(other);
```

---

## Accessing Elements

```java
String first = list.get(0);
int size = list.size();
boolean empty = list.isEmpty();
```

---

## Updating Elements

```java
// Replace element at index
list.set(1, "Charlie");
```

---

## Removing Elements

```java
list.remove("Alice");      // remove by value
list.remove(2);              // remove by index

// Remove all occurrences in another collection
list.removeAll(List.of("X", "Y"));

// Clear entire list
list.clear();
```

---

## Iterating over an ArrayList

```java
// 1. For loop
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i));
}

// 2. Enhanced for
for (String name : list) {
    System.out.println(name);
}

// 3. Iterator
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}

// 4. Streams (Java 8+)
list.forEach(System.out::println);
```

---

## Other Common Methods

| Method                            | Description                                                     |
| --------------------------------- | --------------------------------------------------------------- |
| `contains(Object o)`              | Returns `true` if list contains the element.                    |
| `indexOf(Object o)`               | Returns first index of element or `-1` if not found.            |
| `lastIndexOf(Object o)`           | Returns last index or `-1` if not found.                        |
| `toArray()`                       | Converts to `Object[]`.                                         |
| `<T> T[] toArray(T[] a)`          | Converts to specified array type.                               |
| `trimToSize()`                    | Trims capacity to current size.                                 |
| `ensureCapacity(int minCapacity)` | Increases capacity if needed.                                   |
| `subList(int from, int to)`       | Returns a view between `from` (inclusive) and `to` (exclusive). |

---

## Capacity and Performance

* **Time Complexity**:

  * Access: O(1)
  * Add (at end): Amortized O(1)
  * Insert/Remove (middle): O(n)

* **Resizing**:

  * When capacity is exceeded, capacity grows by roughly 1.5×. Use `ensureCapacity` to avoid frequent resizes.

---

## Converting Between ArrayList and Array

```java
// To Array
String[] arr = list.toArray(new String[0]);

// From Array
String[] data = {"A", "B"};
ArrayList<String> fromArr = new ArrayList<>(Arrays.asList(data));
```

---

## Thread Safety and Synchronization

`ArrayList` is not synchronized. For multi-threaded scenarios, consider:

```java
List<String> syncList = Collections.synchronizedList(new ArrayList<>());
```

Or use `CopyOnWriteArrayList` for better concurrency.

---

## Best Practices and Tips

* **Specify generic type** to avoid raw types.
* **Initial capacity**: Use constructor with capacity if size is known.
* **Avoid frequent resizing**: Call `ensureCapacity` before bulk inserts.
* **Use `List` interface** as reference type to allow easy swapping of implementations.
* **Prefer `subList`** for slicing rather than manual loops.

---

## Full Example

```java
import java.util.*;

public class ArrayListDemo {
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<>(Arrays.asList("Apple", "Banana", "Cherry"));
        fruits.add("Date");
        fruits.add(1, "Blueberry");

        System.out.println("Fruits: " + fruits);
        System.out.println("Contains Cherry? " + fruits.contains("Cherry"));

        fruits.remove("Banana");
        fruits.set(2, "Cranberry");

        System.out.println("After updates: " + fruits);

        System.out.println("Iterate:");
        fruits.forEach(System.out::println);

        String[] array = fruits.toArray(new String[0]);
        System.out.println("As array: " + Arrays.toString(array));
    }
}
```


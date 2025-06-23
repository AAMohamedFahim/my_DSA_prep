# LinkedList in Java

A comprehensive guide to using `LinkedList` in Java. This document covers everything you need to know, from the fundamentals of linked list structures to Java's built-in `LinkedList` class in the Collections Framework.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [What is a Linked List?](#what-is-a-linked-list)
4. [Types of Linked Lists](#types-of-linked-lists)
5. [Creating a LinkedList (Java Built-in)](#creating-a-linkedlist-java-built-in)
6. [Adding & Removing Elements](#adding--removing-elements)
7. [Accessing & Iterating](#accessing--iterating)
8. [Comparison with ArrayList](#comparison-with-arraylist)
9. [Common Methods Overview](#common-methods-overview)
10. [Performance Considerations](#performance-considerations)
11. [Full Example](#full-example)

---

## Introduction

`LinkedList` is a part of Java's `java.util` package that implements a **doubly-linked list**. It allows for efficient insertion and deletion of elements, especially at the beginning or end of the list.

Key characteristics:

* **Doubly Linked**: Each node contains references to both the previous and next node.
* **Implements List, Queue, Deque** interfaces.
* **Not Synchronized**: Use `Collections.synchronizedList()` if thread safety is required.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later.
* Understanding of objects, references, and Java Collections Framework basics.

---

## What is a Linked List?

A **linked list** is a linear data structure made of **nodes**, where each node contains:

* The **data**
* A **reference** (or pointer) to the next node (and optionally previous in doubly-linked)

Unlike arrays, linked lists do **not store data in contiguous memory**, and size can grow/shrink dynamically.

---

## Types of Linked Lists

1. **Singly Linked List**

   * Each node has one reference: to the next node
   * Traversal is forward only

2. **Doubly Linked List**

   * Each node has two references: next and previous
   * Allows forward and backward traversal

3. **Circular Linked List**

   * Last node points back to head (can be singly or doubly circular)
   * Used in round-robin scheduling

---

## Creating a LinkedList (Java Built-in)

```java
import java.util.LinkedList;

LinkedList<String> list = new LinkedList<>();
```

Other ways to initialize:

```java
LinkedList<Integer> numbers = new LinkedList<>(List.of(1, 2, 3));
```

---

## Adding & Removing Elements

```java
// Add to end
list.add("Apple");

// Add to front or end
list.addFirst("Banana");
list.addLast("Cherry");

// Remove from front or end
list.removeFirst();
list.removeLast();

// Remove by index or value
list.remove(1);
list.remove("Apple");
```

---

## Accessing & Iterating

```java
// Access by index
String fruit = list.get(0);

// Loop through
for (String item : list) {
    System.out.println(item);
}

// Using iterator
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

---

## Comparison with ArrayList

| Feature       | LinkedList       | ArrayList       |
| ------------- | ---------------- | --------------- |
| Access Time   | O(n)             | O(1)            |
| Insert/Delete | O(1) (start/end) | O(n) (shifting) |
| Memory Use    | More (node refs) | Less            |
| Random Access | Slower           | Faster          |
| Use-case      | Queues, Stacks   | Indexed data    |

---

## Common Methods Overview

| Method                     | Description                   |
| -------------------------- | ----------------------------- |
| `add()`, `addFirst()`      | Add element to end or front   |
| `remove()`, `removeLast()` | Remove element from end/front |
| `get(int index)`           | Access element by index       |
| `peek()`, `poll()`         | Queue-style access/removal    |
| `size()`                   | Returns number of elements    |
| `clear()`                  | Removes all elements          |
| `contains(Object o)`       | Checks if element exists      |
| `descendingIterator()`     | Iterates in reverse           |

---

## Performance Considerations

* **Insertions/Deletions** at start/end are O(1)
* **Access by index** is O(n)
* Not suitable for frequent random access (use `ArrayList` instead)
* More memory per element (due to node object overhead)

---

## Full Example

```java
import java.util.LinkedList;

public class LinkedListDemo {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();

        list.add("Alpha");
        list.addFirst("Start");
        list.addLast("End");

        System.out.println("First: " + list.getFirst());
        System.out.println("Last: " + list.getLast());

        list.removeFirst();
        list.removeLast();

        for (String val : list) {
            System.out.println(val);
        }
    }
}
```

---

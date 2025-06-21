# StringBuilder in Java

A comprehensive guide to using `StringBuilder` in Java. This document covers everything you need to know, from basic creation to advanced operations and performance considerations.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Creating a StringBuilder](#creating-a-stringbuilder)
4. [Appending & Inserting](#appending--inserting)
5. [Updating & Deleting Content](#updating--deleting-content)
6. [Capacity Management](#capacity-management)
7. [Conversion to String](#conversion-to-string)
8. [Comparison with String and StringBuffer](#comparison-with-string-and-stringbuffer)
9. [Common Methods Overview](#common-methods-overview)
10. [Performance Considerations](#performance-considerations)
11. [Full Example](#full-example)

---

## Introduction

`StringBuilder` is a mutable sequence of characters provided by Java for efficient string manipulation. Unlike `String`, it can be modified without creating new objects, making it ideal for scenarios with frequent or large-scale concatenations.

Key characteristics:

* **Mutable**: Modifiable character sequence.
* **Not Synchronized**: Not thread-safe, but faster than `StringBuffer`.
* **Automatic Resizing**: Internally manages capacity growth.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later.
* Understanding of Java collections and basic I/O.

---

## Creating a StringBuilder

```java
// Empty StringBuilder with default capacity (16)
StringBuilder sb1 = new StringBuilder();

// With initial capacity
StringBuilder sb2 = new StringBuilder(50);

// From existing String
StringBuilder sb3 = new StringBuilder("Initial text");
```

---

## Appending & Inserting

```java
StringBuilder sb = new StringBuilder();

// Append various types
sb.append("Hello");                  // String
sb.append(' ');                         // char
sb.append(123);                         // int
sb.append(45.6);                        // double

// Chaining appends
sb.append(" ").append("World").append('!');

// Insert at specific index
sb.insert(5, ", Java");               // inserts ", Java" at index 5
```

---

## Updating & Deleting Content

```java
// Replace substring between start (inclusive) and end (exclusive)
sb.replace(0, 5, "Hi");                

// Delete characters
sb.delete(2, 6);                         // remove from index 2 to 5

// Delete single char
sb.deleteCharAt(2);

// Reverse
sb.reverse();                            // reverses sequence
```

---

## Capacity Management

```java
int cap = sb.capacity();                // current capacity
int len = sb.length();                  // current length

// Ensure minimum capacity
sb.ensureCapacity(100);

// Trim capacity to current length
sb.trimToSize();
```

---

## Conversion to String

```java
String result = sb.toString();          // convert to immutable String
```

---

## Comparison with String and StringBuffer

| Feature              | StringBuilder   | StringBuffer       | String         |
| -------------------- | --------------- | ------------------ | -------------- |
| Mutability           | Mutable         | Mutable            | Immutable      |
| Thread-safety        | No              | Yes (synchronized) | N/A            |
| Performance (concat) | Fastest         | Slower             | Slow           |
| Use-case             | Single-threaded | Multi-threaded     | Immutable data |

---

## Common Methods Overview

| Method                                | Description                                   |
| ------------------------------------- | --------------------------------------------- |
| `append(...)`                         | Appends text/primitive/object.                |
| `insert(int offset, ...)`             | Inserts text/primitive/object at offset.      |
| `replace(int start, int end, String)` | Replaces characters in range.                 |
| `delete(int start, int end)`          | Deletes characters in range.                  |
| `deleteCharAt(int index)`             | Deletes character at index.                   |
| `reverse()`                           | Reverses character sequence.                  |
| `capacity()`                          | Returns current capacity.                     |
| `length()`                            | Returns current length.                       |
| `ensureCapacity(int minimumCapacity)` | Ensures capacity is at least minimumCapacity. |
| `trimToSize()`                        | Trims capacity to current length.             |
| `toString()`                          | Converts to immutable `String`.               |

---

## Performance Considerations

* **Amortized Growth**: When capacity is exceeded, it increases roughly by `(oldCapacity * 2) + 2`.
* **Single-Threaded**: Best used in environments without concurrent modifications.
* **Avoid Unnecessary Conversions**: Minimize calls to `toString()` inside loops.

---

## Full Example

```java
public class StringBuilderDemo {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Start");
        sb.append(" - Middle").append(" - End");
        System.out.println(sb.toString());

        // Insert
        sb.insert(6, "[Inserted]");
        System.out.println(sb);

        // Replace
        sb.replace(0, 5, "Begin");
        System.out.println(sb);

        // Delete
        sb.delete(5, 15);
        System.out.println(sb);

        // Reverse
        sb.reverse();
        System.out.println("Reversed: " + sb);
    }
}
```

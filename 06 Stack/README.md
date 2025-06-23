# Stack in Java

A comprehensive guide to using `Stack` in Java. This document covers everything you need to know—from fundamental concepts to using Java's built-in `Stack` class and alternatives like `Deque`.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [What is a Stack?](#what-is-a-stack)
4. [Stack Operations](#stack-operations)
5. [Creating a Stack (Java Built-in)](#creating-a-stack-java-built-in)
6. [Pushing & Popping Elements](#pushing--popping-elements)
7. [Peeking & Checking](#peeking--checking)
8. [Deque as Stack (Recommended)](#deque-as-stack-recommended)
9. [Common Use-Cases](#common-use-cases)
10. [Common Methods Overview](#common-methods-overview)
11. [Performance Considerations](#performance-considerations)
12. [Full Example](#full-example)

---

## Introduction

A `Stack` is a linear data structure that follows the **LIFO (Last-In, First-Out)** principle. The last element added to the stack is the first one to be removed.

Java provides both a legacy `Stack` class and modern alternatives like `Deque` (from `ArrayDeque`), which is preferred due to better performance.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later
* Understanding of classes, objects, and basic collections

---

## What is a Stack?

A Stack is a container of objects that are inserted and removed according to the **LIFO** principle.

Operations:

* **Push**: Insert an item onto the top of the stack
* **Pop**: Remove the item from the top
* **Peek**: View the item at the top without removing

Real-world analogies:

* Pile of books
* Undo history in text editors
* Browser navigation history

---

## Stack Operations

| Operation | Description                   | Time Complexity |
| --------- | ----------------------------- | --------------- |
| push      | Add an element                | O(1)            |
| pop       | Remove and return top element | O(1)            |
| peek      | Return top element            | O(1)            |
| isEmpty   | Check if stack is empty       | O(1)            |

---

## Creating a Stack (Java Built-in)

```java
import java.util.Stack;

Stack<Integer> stack = new Stack<>();
```

---

## Pushing & Popping Elements

```java
// Push elements
stack.push(10);
stack.push(20);
stack.push(30);

// Pop element
int top = stack.pop(); // 30
```

---

## Peeking & Checking

```java
// Peek top element
int peeked = stack.peek();

// Check if empty
boolean empty = stack.isEmpty();

// Search for an element (1-based index)
int position = stack.search(20); // returns position from top
```

---

## Deque as Stack (Recommended)

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<Integer> stack = new ArrayDeque<>();

stack.push(100);
stack.pop();
stack.peek();
```

**Why prefer Deque?**

* `ArrayDeque` is faster and more memory-efficient
* No legacy overhead like `Stack` (which is synchronized)

---

## Common Use-Cases

* **Expression evaluation** (postfix, infix)
* **Undo/Redo operations**
* **Balanced parentheses/brackets**
* **Backtracking algorithms** (DFS, recursion simulation)
* **Reversing strings or data**

---

## Common Methods Overview

| Method             | Description                       |
| ------------------ | --------------------------------- |
| `push(E item)`     | Pushes an item onto the top       |
| `pop()`            | Removes and returns top item      |
| `peek()`           | Returns top item without removing |
| `isEmpty()`        | Checks if stack is empty          |
| `search(Object o)` | Finds 1-based position from top   |

---

## Performance Considerations

* All basic operations are **O(1)**
* `Stack` is synchronized — slower in single-threaded apps
* `Deque` (ArrayDeque) is **non-synchronized** and preferred

---

## Full Example

```java
import java.util.Stack;

public class StackDemo {
    public static void main(String[] args) {
        Stack<String> stack = new Stack<>();

        stack.push("Apple");
        stack.push("Banana");
        stack.push("Cherry");

        System.out.println("Top element: " + stack.peek());

        stack.pop();
        System.out.println("After pop: " + stack.peek());

        System.out.println("Is empty: " + stack.isEmpty());
    }
}
```

---

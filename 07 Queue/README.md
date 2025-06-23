# Queue in Java

A comprehensive guide to using `Queue` in Java. This document covers everything from queue fundamentals to Java’s built-in `Queue` interface and its key implementations like `LinkedList` and `ArrayDeque`.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [What is a Queue?](#what-is-a-queue)
4. [Queue Operations](#queue-operations)
5. [Creating a Queue (Java Built-in)](#creating-a-queue-java-built-in)
6. [Adding & Removing Elements](#adding--removing-elements)
7. [Peeking & Checking](#peeking--checking)
8. [Types of Queues](#types-of-queues)
9. [Common Use-Cases](#common-use-cases)
10. [Common Methods Overview](#common-methods-overview)
11. [Performance Considerations](#performance-considerations)
12. [Full Example](#full-example)

---

## Introduction

A `Queue` is a linear data structure that follows the **FIFO (First-In, First-Out)** principle. Elements are added at the rear (tail) and removed from the front (head).

Java provides the `Queue` interface in the `java.util` package with various implementations like `LinkedList`, `PriorityQueue`, and `ArrayDeque`.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later
* Basic knowledge of interfaces and Java collections

---

## What is a Queue?

A **Queue** is a collection designed for holding elements prior to processing.

**FIFO Behavior:**

* **Enqueue**: Add element to the rear
* **Dequeue**: Remove element from the front

Real-life examples:

* People standing in a line
* Printer job scheduling
* Order processing systems

---

## Queue Operations

| Operation | Description                       | Time Complexity |
| --------- | --------------------------------- | --------------- |
| add()     | Inserts element at rear           | O(1)            |
| remove()  | Removes and returns front element | O(1)            |
| peek()    | Returns front element             | O(1)            |
| isEmpty() | Checks if the queue is empty      | O(1)            |

---

## Creating a Queue (Java Built-in)

```java
import java.util.Queue;
import java.util.LinkedList;

Queue<Integer> queue = new LinkedList<>();
```

You can also use `ArrayDeque`:

```java
Queue<Integer> queue = new ArrayDeque<>();
```

---

## Adding & Removing Elements

```java
// Enqueue elements
queue.add(10);
queue.offer(20);
queue.add(30);

// Dequeue element
int removed = queue.remove(); // 10
int polled = queue.poll();    // 20
```

---

## Peeking & Checking

```java
// Peek at front
int front = queue.peek();

// Check if empty
boolean empty = queue.isEmpty();
```

---

## Types of Queues

1. **Simple Queue (FIFO)**

   * Basic queue operations: add, remove, peek

2. **Deque (Double-Ended Queue)**

   * Allows insertion/removal at both ends
   * Use: `ArrayDeque`

3. **PriorityQueue**

   * Elements ordered using natural order or comparator
   * Not FIFO, but based on priority

4. **Circular Queue**

   * Fixed size, wraps around when full
   * Useful in buffering systems (not directly available in Java, needs custom implementation)

---

## Common Use-Cases

* **Task scheduling**
* **Breadth-First Search (BFS)**
* **Request buffering**
* **Resource management**
* **Producer-Consumer problems**

---

## Common Methods Overview

| Method       | Description                                      |
| ------------ | ------------------------------------------------ |
| `add(E e)`   | Inserts the element (throws if fails)            |
| `offer(E e)` | Inserts the element (returns false if fails)     |
| `remove()`   | Retrieves and removes the head (throws if empty) |
| `poll()`     | Retrieves and removes the head (null if empty)   |
| `peek()`     | Retrieves but does not remove the head           |
| `element()`  | Like peek(), but throws if queue is empty        |
| `isEmpty()`  | Checks if queue is empty                         |

---

## Performance Considerations

* `LinkedList` and `ArrayDeque` both offer O(1) time for enqueue/dequeue
* `PriorityQueue` uses a heap → O(log n) for insert/remove
* `ArrayDeque` is faster and more memory efficient than `LinkedList`

---

## Full Example

```java
import java.util.Queue;
import java.util.LinkedList;

public class QueueDemo {
    public static void main(String[] args) {
        Queue<String> queue = new LinkedList<>();

        queue.add("Apple");
        queue.add("Banana");
        queue.offer("Cherry");

        System.out.println("Front: " + queue.peek());

        queue.remove();
        System.out.println("After removal: " + queue.peek());

        while (!queue.isEmpty()) {
            System.out.println(queue.poll());
        }
    }
}
```

---

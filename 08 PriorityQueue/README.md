# PriorityQueue in Java

A comprehensive guide to using `PriorityQueue` in Java. This document covers its internal working, usage, and best practices, along with a complete overview of methods and performance insights. This guide is designed so that if you are learning `PriorityQueue` for the first time, you won’t need to refer to any other resource.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [What is a PriorityQueue?](#what-is-a-priorityqueue)
4. [How it Works](#how-it-works)
5. [Creating a PriorityQueue](#creating-a-priorityqueue)
6. [Adding & Removing Elements](#adding--removing-elements)
7. [Custom Comparator Usage](#custom-comparator-usage)
8. [Common Use-Cases](#common-use-cases)
9. [Common Methods Overview](#common-methods-overview)
10. [Performance Considerations](#performance-considerations)
11. [Full Example](#full-example)

---

## Introduction

A `PriorityQueue` is a special type of queue in Java where elements are ordered by their **priority** rather than insertion order. It does **not** follow FIFO behavior.

Java’s `PriorityQueue` is implemented using a **binary heap**.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later
* Understanding of generics, collections, and comparators

---

## What is a PriorityQueue?

A `PriorityQueue` is an abstract data type where each element is associated with a priority and is served based on the priority.

* **Min-Heap by Default**: The smallest element is always at the front.
* **No null elements allowed**
* **Unbounded size**: Grows as needed

> Think of it like a task manager where tasks with higher importance (lower number in case of min-heap) get executed first.

---

## How it Works

Internally, a `PriorityQueue` uses a **binary heap** structure:

* Add: Element is added to the end and then heapified
* Remove: The root (min element) is removed and the heap is rebalanced

### Additional Explanation:

* The underlying structure is a complete binary tree represented as an array.
* When an element is added (`add()`/`offer()`), it is placed at the end of the array.
* A "heapify-up" (also known as "bubble-up") process is triggered to maintain the heap property. This compares the added element with its parent and swaps if necessary.
* When the head element is removed (`remove()`/`poll()`), the last element in the array is moved to the root.
* Then a "heapify-down" (also known as "bubble-down") occurs, where the new root is compared with its children and swapped with the smaller one to maintain the min-heap property.

#### Key Characteristics:

* The heap is **complete**, meaning all levels are filled except possibly the last, and nodes are left-aligned.
* **No duplicates restriction**: You can have duplicate values.
* **Dynamic resizing**: Internally resizes the backing array as needed.

#### Visual Example:

If you insert the elements \[10, 4, 8, 3] in a `PriorityQueue`, it may internally rearrange to \[3, 4, 8, 10] based on priority.

---

## Creating a PriorityQueue

```java
import java.util.PriorityQueue;

PriorityQueue<Integer> pq = new PriorityQueue<>();
```

With initial capacity:

```java
PriorityQueue<Integer> pq = new PriorityQueue<>(20);
```

With custom comparator (Max-Heap):

```java
PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> b - a);
```

---

## Adding & Removing Elements

```java
// Add elements
pq.add(10);
pq.add(5);
pq.offer(15);

// Peek smallest (min-heap)
System.out.println(pq.peek()); // 5

// Remove elements
pq.remove();  // Removes 5
pq.poll();    // Removes 10
```

---

## Custom Comparator Usage

```java
import java.util.PriorityQueue;

PriorityQueue<String> pq = new PriorityQueue<>((a, b) -> a.length() - b.length());

pq.add("Java");
pq.add("DSA");
pq.add("Queue");

System.out.println(pq.peek()); // DSA (shortest length)
```

You can customize sorting by:

* Length
* Reverse order
* Frequency

---

## Common Use-Cases

* **Dijkstra’s shortest path algorithm**
* **Top K elements problems**
* **Merging K sorted lists**
* **Task/job scheduling**
* **Custom sorting operations**

---

## Common Methods Overview

| Method       | Description                                    |
| ------------ | ---------------------------------------------- |
| `add(E e)`   | Inserts element, throws if not possible        |
| `offer(E e)` | Inserts element, returns false if not possible |
| `peek()`     | Returns the head element without removing it   |
| `poll()`     | Retrieves and removes the head of the queue    |
| `remove()`   | Removes the head, throws if empty              |
| `isEmpty()`  | Returns true if the queue is empty             |

---

## Performance Considerations

* Insertions and deletions take **O(log n)** time
* Retrieval with `peek()` takes **O(1)**
* Backed by binary heap (array-based)
* Not thread-safe (use `PriorityBlockingQueue` in concurrent scenarios)

---

## Full Example

```java
import java.util.PriorityQueue;

public class PriorityQueueDemo {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();

        pq.add(20);
        pq.add(5);
        pq.add(15);

        System.out.println("Top element (min): " + pq.peek());

        while (!pq.isEmpty()) {
            System.out.println(pq.poll());
        }
    }
}
```

---

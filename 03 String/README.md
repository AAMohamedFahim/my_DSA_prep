# Strings in Java

A comprehensive guide to using `String` in Java. This document covers everything you need to know, from basic creation to advanced operations and performance considerations.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Creating Strings](#creating-strings)
4. [Accessing Characters](#accessing-characters)
5. [Length and emptiness](#length-and-emptiness)
6. [String Comparison](#string-comparison)
7. [Searching and Substrings](#searching-and-substrings)
8. [Concatenation & Formatting](#concatenation--formatting)
9. [Conversion to/from Other Types](#conversion-tofrom-other-types)
10. [Immutability & Performance](#immutability--performance)
11. [StringBuilder & StringBuffer](#stringbuilder--stringbuffer)
12. [Common Methods Overview](#common-methods-overview)
13. [Full Example](#full-example)

---

## Introduction

In Java, `String` is a final, immutable class representing a sequence of characters. Strings are widely used for text manipulation, I/O operations, and configuration. Since they are immutable, any operation that seems to modify a string actually creates a new one.

Key characteristics:

* **Immutable**: Once created, the value cannot change.
* **Stored in String Pool**: Literals are interned for memory efficiency.
* **Thread-safe**: Due to immutability.

---

## Prerequisites

* Java Development Kit (JDK) 8 or later.
* Basic understanding of Java syntax and object-oriented principles.

---

## Creating Strings

```java
// String literal (interned)
String s1 = "Hello";

// Using constructor (new object)
String s2 = new String("Hello");

// From char array
char[] chars = {'J','a','v','a'};
String s3 = new String(chars);

// From byte array (specify charset)
byte[] bytes = {65, 66, 67};
String s4 = new String(bytes, StandardCharsets.UTF_8);  // "ABC"
```

---

## Accessing Characters

```java
char first = s1.charAt(0);        // 'H'
char[] arr = s1.toCharArray();    // ['H','e','l','l','o']
```

---

## Length and emptiness

```java
int len = s1.length();            // 5
boolean empty = s1.isEmpty();     // false
```

---

## String Comparison

```java
String a = "test";
String b = new String("test");

// Reference check (not recommended)
bool eqRef = (a == b);            // false

// Value check (use equals)
bool eqVal = a.equals(b);         // true

// Case-insensitive
a.equalsIgnoreCase("Test");     // true
```

---

## Searching and Substrings

```java
String phrase = "Hello World";

// Contains
bool hasHello = phrase.contains("Hello");

// Index
int idx = phrase.indexOf('o');      // 4
int last = phrase.lastIndexOf("or"); // 7

// Substring
String sub = phrase.substring(6);      // "World"
String part = phrase.substring(0,5);   // "Hello"
```

---

## Concatenation & Formatting

```java
// Concatenation
String s = "Hi" + ", " + "there!";

// Using concat method
s = "Hello".concat("Java");

// String.format
default locale
String out = String.format("Name: %s, Age: %d", "Alice", 30);

// printf (System.out)
System.out.printf("PI ~ %.2f", Math.PI);
```

---

## Conversion to/from Other Types

```java
// To upper/lower case
String up = s1.toUpperCase();
String low = s1.toLowerCase();

// Trim whitespace
String t = "  abc  ".trim();  // "abc"

// Split
dString[] parts = "a,b,c".split(",");

// ValueOf (primitive to String)
String num = String.valueOf(123);

// Parse (String to primitive)
int x = Integer.parseInt("456");
double d = Double.parseDouble("3.14");
```

---

## Immutability & Performance

* **Memory**: each modification creates a new object.
* **String Pool**: literals reuse memory via interning.
* **Concatenation in loops**: avoid `+` in a loop—use `StringBuilder` to prevent O(n²) behavior.

---

## StringBuilder & StringBuffer

When you need mutable strings:

```java
// StringBuilder (not synchronized)
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(' ');
sb.append("World");
String result = sb.toString();

// StringBuffer (synchronized)
StringBuffer sbuf = new StringBuffer(); // thread-safe
```

---

## Common Methods Overview

| Method                                        | Description                             |
| --------------------------------------------- | --------------------------------------- |
| `charAt(int index)`                           | Returns character at specified index.   |
| `compareTo(String another)`                   | Lexicographically compares two strings. |
| `equals(Object obj)`                          | Checks value equality.                  |
| `equalsIgnoreCase(String ig)`                 | Case-insensitive equality.              |
| `contains(CharSequence s)`                    | Checks if substring exists.             |
| `matches(String regex)`                       | Checks regex match.                     |
| `replace(CharSequence old, CharSequence rep)` | Replaces occurrences.                   |
| `split(String regex)`                         | Splits into array by regex.             |
| `substring(int begin, int end)`               | Returns subsequence.                    |
| `toCharArray()`                               | Converts to char array.                 |
| `trim()`                                      | Trims leading/trailing whitespace.      |
| `valueOf(...)`                                | Converts primitives/objects to String.  |
| `intern()`                                    | Interns the string in the pool.         |

---

## Full Example

```java
public class StringDemo {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = s1 + " World";
        System.out.println("s2: " + s2);

        System.out.println("Length: " + s2.length());
        System.out.println("Char at 1: " + s2.charAt(1));

        if (s2.contains("World")) {
            System.out.println("Found 'World'");
        }

        String[] words = s2.split(" ");
        System.out.println("Words: " + Arrays.toString(words));

        // Using StringBuilder
        StringBuilder sb = new StringBuilder();
        for (String w : words) {
            sb.append(w).append("#");
        }
        System.out.println("Joined with #: " + sb.toString());
    }
}
```


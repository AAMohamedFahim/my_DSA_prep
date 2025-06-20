# Types of Arrays in Java

1. **Single-Dimensional Array**
   - Example: `int[] numbers = new int[5];`
   - Stores elements in a linear sequence.

2. **Multi-Dimensional Array**
   - Usually 2D arrays or more (arrays of arrays).
   - Example: `int[][] matrix = new int[3][3];`
   - Used to represent tables or matrices.

3. **Jagged Arrays**
   - An array of arrays where each sub-array can have a different length.
   - Example:
     ```java
     int[][] jaggedArray = new int[3][];
     jaggedArray[0] = new int[2];
     jaggedArray[1] = new int[4];
     jaggedArray[2] = new int[3];
     ```
---

---

## Operations Overview

Below are the core operations you’ll perform on Java arrays:

1. **Declaration & Creation** – defining the array type and allocating memory.
2. **Access & Update** – reading and writing elements by index.
3. **Traversal** – iterating over elements (for‑loop, enhanced for, streams).
4. **Search** – linear scan or binary search on sorted arrays.
5. **Sorting** – ordering elements via `Arrays.sort`.
6. **Copying & Resizing** – duplicating or extending arrays with `Arrays.copyOf`.
7. **Filling** – setting all elements to a specific value using `Arrays.fill`.
8. **Equality Check** – comparing arrays with `Arrays.equals`/`deepEquals`.
9. **Conversion** – between arrays and collections (`Arrays.asList`, `toArray`).
10. **Multidimensional Handling** – working with 2D (or jagged) arrays.

---

## Operation Examples

### 1. Declaration & Creation

```java
// Declare and allocate
int[] nums = new int[5];                // [0,0,0,0,0]
String[] names = {"Alice", "Bob"};    // ["Alice","Bob"]
```

### 2. Access & Update

```java
int x = nums[2];       // read
nums[0] = 10;           // write
```

### 3. Traversal

```java
// Traditional loop
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}
// Enhanced for
for (String name : names) {
    System.out.println(name);
}
```

### 4. Search

```java
// Linear search
target: for (int i = 0; i < nums.length; i++) {
    if (nums[i] == 10) {
        System.out.println("Found at index " + i);
        break target;
    }
}
// Binary search (sorted array)
Arrays.sort(nums);
int idx = Arrays.binarySearch(nums, 10);
```

### 5. Sorting

```java
Arrays.sort(nums);                // ascending
Arrays.sort(names, Collections.reverseOrder()); // descending
```

### 6. Copying & Resizing

```java
int[] copy = Arrays.copyOf(nums, nums.length);
int[] larger = Arrays.copyOf(nums, nums.length + 3); // padded with 0s
```

### 7. Filling

```java
Arrays.fill(nums, -1);
```

### 8. Equality Check

```java
boolean eq = Arrays.equals(nums, copy);
boolean deep = Arrays.deepEquals(new Object[][]{{"a"}}, new Object[][]{{"a"}});
```

### 9. Conversion

```java
List<String> list = Arrays.asList(names);
String[] back = list.toArray(new String[0]);
```

### 10. Multidimensional Handling

```java
int[][] matrix = {{1,2,3},{4,5,6}};
for (int[] row : matrix) {
    System.out.println(Arrays.toString(row));
}
```

---

## 1. Introduction

An **array** in Java is a container object that holds a fixed number of values of a single type. The length of an array is established when the array is created. You cannot change its length once created.

Key characteristics:

* Homogeneous: all elements share the same type.
* Fixed size: length cannot be altered.
* Zero-based indexing: first element at index `0`, last at `length - 1`.

Arrays provide a foundation for many algorithms and data structures and are frequently used in both production code and technical interviews.

---

---

## 15. Array Methods & Functions

Java provides a rich set of **utility methods** for array manipulation and analysis via the `java.util.Arrays` class:

| Method Signature                                          | Description                                                                   |
| --------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `void sort(int[] a)`                                      | Sorts the specified array of ints in ascending order.                         |
| `void sort(int[] a, int fromIndex, int toIndex)`          | Sorts the specified range (`[fromIndex, toIndex)`) in the array.              |
| `void parallelSort(long[] a)`                             | Sorts the array using parallel sorting (fork/join) for large arrays.          |
| `<T> void sort(T[] a, Comparator<? super T> c)`           | Sorts object array using provided comparator.                                 |
| `int binarySearch(int[] a, int key)`                      | Searches for `key` in a sorted array; returns index or `-(insertionPoint)-1`. |
| `int binarySearch(T[] a, T key, Comparator<? super T> c)` | Searches with comparator in a sorted array of objects.                        |
| `boolean equals(int[] a, int[] b)`                        | Returns `true` if both arrays are element‑wise equal.                         |
| `boolean deepEquals(Object[] a, Object[] b)`              | Returns `true` if two nested arrays are deeply equal.                         |
| `int mismatch(int[] a, int[] b)`                          | Returns the first index where arrays differ, or `-1` if identical.            |
| `int[] copyOf(int[] original, int newLength)`             | Copies array, truncating or padding with zeros to `newLength`.                |
| `<T> T[] copyOfRange(T[] original, int from, int to)`     | Copies specified range into new array of type `T`.                            |
| `void fill(boolean[] a, boolean val)`                     | Assigns `val` to each element of the array.                                   |
| `void setAll(int[] a, IntUnaryOperator generator)`        | Sets each element using the generator function applied to its index.          |
| `void parallelPrefix(int[] a, IntBinaryOperator op)`      | Performs a cumulative operation (`op`) on elements in parallel.               |
| `String toString(Object[] a)`                             | Returns a one‑dimensional array’s string representation.                      |
| `String deepToString(Object[] a)`                         | Returns nested arrays’ string representation.                                 |
| `<T> List<T> asList(T... a)`                              | Returns a fixed‑size list backed by the specified array (not resizable).      |
| `Stream<T> stream(T[] a)`                                 | Returns a sequential `Stream` over the array elements (Java 8+).              |
| `Stream<T> parallelStream(T[] a)`                         | Returns a parallel `Stream` over the array elements (Java 8+).                |
| `Spliterator<T> spliterator(T[] a)`                       | Returns a `Spliterator` for the array, enabling advanced iteration.           |
| `long hashCode(int[] a)`                                  | Returns a hash code based on the contents of the array.                       |
| `long deepHashCode(Object[] a)`                           | Returns a deep hash code for nested arrays.                                   |

---

## 16. Example Code for Array Methods & Functions

Below are individual code shells demonstrating each utility method separately.

### 16.1 `void sort(int[] a)`

```java
int[] nums = {3, 1, 2};
Arrays.sort(nums);
// nums: [1, 2, 3]
```

### 16.2 `void sort(int[] a, int fromIndex, int toIndex)`

```java
int[] arr = {5, 4, 3, 2, 1};
Arrays.sort(arr, 1, 4);
// arr: [5, 2, 3, 4, 1]
```

### 16.3 `void parallelSort(long[] a)`

```java
long[] data = {10L, 30L, 20L};
Arrays.parallelSort(data);
// data: [10, 20, 30]
```

### 16.4 `<T> void sort(T[] a, Comparator<? super T> c)`

```java
String[] names = {"Bob", "Alice", "Charlie"};
Arrays.sort(names, Comparator.reverseOrder());
// names: ["Charlie", "Bob", "Alice"]
```

### 16.5 `int binarySearch(int[] a, int key)`

```java
int idx = Arrays.binarySearch(nums, 2);
// idx: 1
```

### 16.6 `int binarySearch(T[] a, T key, Comparator<? super T> c)`

```java
int sidx = Arrays.binarySearch(names, "Bob", Comparator.reverseOrder());
// sidx: 1
```

### 16.7 `boolean equals(int[] a, int[] b)`

```java
boolean isEqual = Arrays.equals(nums, new int[]{1,2,3});
// isEqual: true
```

### 16.8 `boolean deepEquals(Object[] a, Object[] b)`

```java
Integer[][] m1 = {{1,2}, {3,4}};
Integer[][] m2 = {{1,2}, {3,4}};
boolean deepEq = Arrays.deepEquals(m1, m2);
// deepEq: true
```

### 16.9 `int mismatch(int[] a, int[] b)`

```java
int mis = Arrays.mismatch(new int[]{1,2,3}, new int[]{1,0,3});
// mis: 1
```

### 16.10 `int[] copyOf(int[] original, int newLength)`

```java
int[] copy = Arrays.copyOf(nums, 5);
// copy: [1,2,3,0,0]
```

### 16.11 `<T> T[] copyOfRange(T[] original, int from, int to)`

```java
String[] sub = Arrays.copyOfRange(names, 0, 2);
// sub: ["Charlie","Bob"]
```

### 16.12 `void fill(boolean[] a, boolean val)`

```java
boolean[] flags = new boolean[3];
Arrays.fill(flags, true);
// flags: [true, true, true]
```

### 16.13 `void setAll(int[] a, IntUnaryOperator generator)`

```java
int[] squares = new int[5];
Arrays.setAll(squares, i -> i * i);
// squares: [0,1,4,9,16]
```

### 16.14 `void parallelPrefix(int[] a, IntBinaryOperator op)`

```java
int[] prefix = {1,2,3,4};
Arrays.parallelPrefix(prefix, (x,y) -> x + y);
// prefix: [1,3,6,10]
```

### 16.15 `String toString(Object[] a)`

```java
String s = Arrays.toString(names);
// s: "[Charlie, Bob, Alice]"
```

### 16.16 `String deepToString(Object[] a)`

```java
String ds = Arrays.deepToString(m1);
// ds: "[[1, 2], [3, 4]]"
```

### 16.17 `<T> List<T> asList(T... a)`

```java
List<String> list = Arrays.asList("X", "Y");
// list: [X, Y]
```

### 16.18 `Stream<T> stream(T[] a)`

```java
int sum = Arrays.stream(nums).sum();
// sum: 6
```

### 16.19 `Stream<T> parallelStream(T[] a)`

```java
int count = (int) Arrays.stream(nums).parallel().filter(n -> n > 1).count();
// count: 2
```

### 16.20 `Spliterator<T> spliterator(T[] a)`

```java
Spliterator<Integer> spl = Arrays.spliterator(new Integer[]{1,2,3});
spl.forEachRemaining(System.out::println);
```

### 16.21 `long hashCode(int[] a)`

```java
long hc = Arrays.hashCode(nums);
// hc: some hash value
```

### 16.22 `long deepHashCode(Object[] a)`

```java
long dhc = Arrays.deepHashCode(new Object[]{new int[]{1,2}});
// dhc: some deep hash value
```

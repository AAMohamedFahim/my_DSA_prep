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

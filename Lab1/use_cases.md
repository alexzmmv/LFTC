# Mini Language Use Cases (Concise)

Domain focus: small in-memory data filtering & transformation (e.g., lists of sensor readings).

## 1. Assignment
Purpose: Store intermediate or final computed values for reuse.
Example:
```
avg = (sum + last) / count;
```
Justification: Enables naming results instead of recomputing expressions.

## 2. If / Else
Purpose: Conditional branching for data-dependent actions.
Example:
```
!! SIMPLE IF-ELSE
if (value > threshold) {
  put("ALERT");
} else {
  put("OK");
}

!! NESTED IF-ELSE (UNAMBIGUOUS)
if (temp > high) {
  if (humidity > 80) {
    put("CRITICAL");
  } else {
    put("WARNING");  !! else matches nearest if (humidity)
  }
} else {
  put("NORMAL");
}
```
Justification: Required for complex conditional logic with unambiguous nesting.

## 3. For (Counter Loop)
Purpose: Iterative numeric processing (e.g., aggregations by index).
Example:
```
for (i = 0; i < len; i = i + 1) {
  sum = sum + readings[i];
}
```
Justification: Classic indexed iteration for accumulation and transformations.

## 4. Iterate (Foreach over List)
Purpose: Direct traversal of list elements when index not needed.
Example:
```
iterate (r in readings) {
  if (r > max) { max = r; }
}
```
Justification: More readable element-focused loop for scans.

## 5. Print (put)
Purpose: Emit values or messages (debugging/reporting).
Example:
```
put(max);
```
Justification: Minimal output/inspection facility.

## 6. Ternary Expression ? :
Purpose: Inline conditional value selection.
Example:
```
status = (max > threshold) ? "ALERT" : "OK";
```
Justification: Concise conditional assignment without full if/else block.

## 7. List Literals and Indexing
Purpose: Build and access collections for processing.
Example:
```
!! SIMPLE LIST AND INDEXING
readings = [12, 15, 18, 14];
first = readings[0];

!! NESTED LISTS AND MULTI-DIMENSIONAL ACCESS
matrix = [[1, 2], [3, 4]];
cell = matrix[1][0];  !! gets 3
```
Justification: Core data structures with flexible single/multi-dimensional access.

## 8. Comments (!! / !!!)
Purpose: Document logic; multi-line for block notes.
Example:
```
!! THIS IS A SINGLE LINE COMMENT
!!! 
THIS IS A MULTI-LINE COMMENT
WITH UPPERCASE LETTERS
AND NUMBERS 123
!!!
```
Justification: Improves maintainability; ignored by interpreter. Comments must use uppercase letters.

## Minimal End-to-End Snippet
```
readings = [12, 15, 18, 14];
threshold = 16;
sum = 0;
for (i = 0; i < 4; i = i + 1) { sum = sum + readings[i]; }
avg = sum / 4;
max = 0;
iterate (r in readings) { if (r > max) { max = r; } }
status = (max > threshold) ? "ALERT" : "OK";
put(status);
```
Demonstrates: assignment, loops, conditional, ternary, list, print.

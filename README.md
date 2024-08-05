# LEETCODE-Array-2053
Sure! Let's go through a dry run of the given Java code. The task is to find the k-th distinct string in an array of strings. A distinct string is one that appears exactly once in the array.

### Dry Run

Consider the following input:
- `arr = ["a", "b", "a", "c", "b", "d"]`
- `k = 2`

Here's the code again for reference:
```java
class Solution {
  public String kthDistinct(String[] arr, int k) {
    Map<String, Integer> count = new HashMap<>();

    for (final String a : arr)
      count.merge(a, 1, Integer::sum);

    for (final String a : arr)
      if (count.get(a) == 1 && --k == 0)
        return a;

    return "";
  }
}
```

### Step-by-Step Execution

1. **Initialization:**
   - Create a `HashMap` called `count` to store the frequency of each string.

2. **First Loop - Counting Frequencies:**
   - Iterate through the array `arr` and update the `count` map with the frequency of each string.
   - After this loop, the `count` map will look like this:
     ```java
     {
       "a" -> 2,
       "b" -> 2,
       "c" -> 1,
       "d" -> 1
     }
     ```

3. **Second Loop - Finding k-th Distinct String:**
   - Iterate through the array `arr` again to find the k-th distinct string.
   - Initialize `k` with the value 2.
   - Check each string in the array:
     - `"a"`: Frequency is 2 (not distinct).
     - `"b"`: Frequency is 2 (not distinct).
     - `"a"`: Frequency is 2 (not distinct).
     - `"c"`: Frequency is 1 (distinct). Decrement `k` (k becomes 1).
     - `"b"`: Frequency is 2 (not distinct).
     - `"d"`: Frequency is 1 (distinct). Decrement `k` (k becomes 0). Since `k` is now 0, return `"d"`.

So, the 2nd distinct string in the array `arr` is `"d"`.

### Summary
The final output of the function with the given input will be `"d"`.

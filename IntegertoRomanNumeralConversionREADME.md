# leet-day42

## Integer to Roman Numeral Conversion

### Problem Description

Given an integer `num`, convert it to a Roman numeral. The input integer `num` is in the range [1, 3999].

### Approach

The problem requires converting an integer to a Roman numeral using the Roman numeral symbols (I, V, X, L, C, D, M). To achieve this, we can use a greedy approach. We create two arrays: one for the values of the Roman numerals and another for the corresponding symbols. The arrays are ordered from largest to smallest, which ensures that the largest possible value is subtracted from the input integer at each step to form the Roman numeral.

1. Initialize two arrays:
   - `values`: An array containing the values of the Roman numerals in descending order (e.g., 1000, 900, 500, ...).
   - `symbols`: An array containing the corresponding symbols of the Roman numerals (e.g., "M", "CM", "D", ...).

2. Initialize an empty string `result` to store the final Roman numeral.

3. Iterate through the `values` and `symbols` arrays:
   - While the input `num` is greater than or equal to the current `values[i]`:
     - Append the corresponding symbol `symbols[i]` to the `result`.
     - Subtract the current `values[i]` from the `num`.

4. Return the `result` as the converted Roman numeral.

### Code Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>

class Solution {
public:
    std::string intToRoman(int num) {
        std::vector<int> values = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        std::vector<std::string> symbols = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};

        std::string result = "";

        for (int i = 0; i < values.size(); ++i) {
            while (num >= values[i]) {
                result += symbols[i];
                num -= values[i];
            }
        }

        return result;
    }
};

```

### Complexity Analysis

- Time Complexity: O(1) since the number of iterations is constant for the given range.
- Space Complexity: O(1) since the sizes of `values` and `symbols` arrays are constant.

This solution provides an efficient way to convert an integer to a Roman numeral using a greedy approach and pre-defined arrays of values and symbols.

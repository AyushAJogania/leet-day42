# leet-day42

# Problem: Interleaving String

Given strings s1, s2, and s3, determine whether s3 is formed by interleaving s1 and s2.

An interleaving of two strings s and t is a configuration where they are divided into non-empty substrings such that:

s = s1 + s2 + ... + sn
t = t1 + t2 + ... + tm
|n - m| <= 1
The interleaving is s1 + t1 + s2 + t2 + s3 + t3 + ... or t1 + s1 + t2 + s2 + t3 + s3 + ...

## Example

### Input
```
s1 = "aabcc"
s2 = "dbbca"
s3 = "aadbbcbcac"
```
### Output
```
true
```
Explanation: One possible way to obtain s3 is by splitting s1 into "aa" and "bc", and splitting s2 into "dbbc" and "a". Interleaving the substrings, we get "aa" + "dbbc" + "bc" + "a" + "c" = "aadbbcbcac".

## Constraints
- 0 <= s1.length, s2.length <= 100
- 0 <= s3.length <= 200
- s1, s2, and s3 consist of lowercase English letters.

## Approach

To solve this problem, we can use a dynamic programming approach. We'll create a 2D boolean array `dp`, where `dp[i][j]` will be `true` if the first `i` characters of `s1` and the first `j` characters of `s2` can form the first `i+j` characters of `s3`. 

We can iterate through `s1` and `s2` characters, and update the `dp` array accordingly based on whether the current characters match the corresponding character in `s3`.

The base case is when both `s1` and `s2` are empty, then `s3` should also be empty, so `dp[0][0]` will be `true`.

The final answer will be stored in `dp[s1.length()][s2.length()]`.

## Complexity
- Time complexity: O(m*n), where m is the length of `s1` and n is the length of `s2`.
- Space complexity: O(m*n), for the dynamic programming array `dp`.

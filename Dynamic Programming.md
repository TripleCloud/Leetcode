# Dynamic Programming

## 239. Sliding Window Maximum

## 53. Maximum Subarray
- Two Cases:
1. If the maximum of the previous point < 0 (stored in `curr_max`) : then the maximum of the current point is restarted
```python
if curr_max < 0:
	curr_max = nums[i]
```
2. If the maximum of the previous point $\geq$ 0: the maximum of the current point is culmulated
```python
else:
	curr_max += nums[i]
```
- DP Storage: Update the `nums[i]`
`nums[i]` store the global maximum so far: compare the `curr_max` to `nums[i-1]`
```python
nums[i] = max(curr_max, nums[i-1])
```

### Kadane's Algorithm: Maximum Subarray Sum
$$dp[i] = max(dp[i-1], 0) + arr[i]$$
- Base Conditions:
$$ dp[0] = arr[0]$$
- Time Complexity: O(N)
- Space Complexity: O(1)

## 121. Best Time to Buy and Sell Stock
right -> left
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        max_profit = 0
        if n == 0:
            return max_profit
        high_sell = prices[n-1]
        for i in range(1, n + 1):
            if prices[n - i] > high_sell:
                high_sell = prices[n - i]
            elif high_sell - prices[n - i] > max_profit:
                max_profit = high_sell - prices[n - i]
        return max_profi
```
## 5. Longest Palindromic Substring
### Method 1: DP
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        dp = [[False] * len(s) for _ in range(len(s))]
        start_max = end_max = 0
        for i in range(len(s)):
            start = i
            end = i
            while start >= 0:
                if start == end:
                    dp[start][end] = s[start] == s[end]
                elif start + 1 == end:
                    dp[start][end] = s[start] == s[end]
                else:
                    dp[start][end] = dp[start + 1][end - 1] and s[start] == s[end]
                    
                if dp[start][end] and (end - start) > (end_max - start_max):
                    start_max = start
                    end_max = end
                start -= 1
        return s[start_max:end_max+1]
```
Time complexity: O($n^2$)
Space complexity: O($n^2$)

### Method 2: Expand from the center
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        start = end = 0
        for i in range(len(s)):
            odd = self.expand(s, i, i)
            even = self.expand(s, i, i + 1)
            ret = max(odd, even)
            print(ret)
            if ret > (end - start + 1):
                start = i - int((ret -1) / 2)
                end = i + int(ret / 2)
        return s[start:end + 1]
```
Time complexity: O($n^2$)
Space complexity: O($n^2$)


<!--stackedit_data:
eyJoaXN0b3J5IjpbMzA1NzA3NDIyLDUwOTM1NTgzLC03MjgyOT
Q3NDIsMjUyMjExOTA1LC05NDcxNDc3MDZdfQ==
-->
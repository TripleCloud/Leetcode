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
```

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY4NTg3OTYwNiwtNzI4Mjk0NzQyLDI1Mj
IxMTkwNSwtOTQ3MTQ3NzA2XX0=
-->
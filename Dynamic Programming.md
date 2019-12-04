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



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ0MjE4OTY0NiwtOTQ3MTQ3NzA2XX0=
-->
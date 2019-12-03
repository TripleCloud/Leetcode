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
`nums[i]` store the global maximum so far: 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIyMDYzMTc1MywzNTA5MTM3MTAsODk0Nj
QxOTYzLC0yMDg4NzQ2NjEyXX0=
-->
# Dynamic Programming

## 239. Sliding Window Maximum

## 53. Maximum Subarray

If the maximum of the previous point < 0 (stored in `curr_max`) : then the maximum of the current point is restarted
```
if curr_max < 0:
	curr_max = nums[i]
```
If the maximum of the previous point $\geq$ 0: the maximum of the current point is culmulated
```
else:
	curr_max += nums[i]
```
Update

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkyMTc4NjIxOSwzNTA5MTM3MTAsODk0Nj
QxOTYzLC0yMDg4NzQ2NjEyXX0=
-->
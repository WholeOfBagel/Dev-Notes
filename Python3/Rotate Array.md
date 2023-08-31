```python
def rotate(self, nums: List[int], k: int) -> None:
	L = len(nums)
	if L == k: return

	k = k%L # the case when k > L
	nums.reverse()

	for i in range(k//2):
		nums[i], nums[k-1-i] = nums[k-1-i], nums[i]

	for i in range(k, (L+k)//2):
		nums[i], nums[L-1-i+k] = nums[L-1-i+k], nums[i]
```

1. base case where we are simply returning what we have
2. moding is important in getting the minimal change
3. splitting it in half based off of how far we are going to move it
	1. reverse the two parts separately = reforming original structure
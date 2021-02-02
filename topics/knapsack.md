# Knapsack



Given a knapsack and an array of items with weights, determine if you can fill the knapsack completely (each item can only be chosen once).

Pseudocode:
```
knapsack(items, maxSize) {
	dp = [0] * (maxSize + 1)
	
	dp[0] = 1
	for(i = 0; i < items.length; i++)
		for(j = maxSize; j >= items[i]; j--)
			dp[j] |= dp[j - items[i]]      // bitwise OR

	return dp[maxSize]
}
```

Time complexity - O(n\*m) where n is item length, m is maxSize 
<br/>
Space complexity - O(m)

NOTE: If items can be chosen multiple times, then flip the direction of the second loop.
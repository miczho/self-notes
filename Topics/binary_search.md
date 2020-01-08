# Binary Search

Runtime is O(log n) so it's pretty efficient.

Only works if the ordered data is either constantly increasing or decreasing (non-changing is fine too).
- If the condition is viewed as a boolean return, then if the data looks like this (FFFFFFFTTTTTTT), then binary will work.

<br/>

Pseudocode:
```
binary_search(lo, hi) {
	while lo < hi:
		mid = (lo + hi) / 2

		if f(mid) == true:
			hi = mid
		else:
			lo = mid + 1

	if f(lo) == false:
		// there is no solution

	return lo;
}
```

<details>
	<summary>Examples</summary>

Work in progress.

</details>

## Binary Search Tree

This binary tree has a the property s.t. for every node, the left subtree contains values less than the node, and the right subtree contains values greater than the node.

This tree should generally be balanced.
![TEA](../Pictures/bst.png)
# 3Sum (LeetCode 15)

Given an integer array `nums`, return all the **unique triplets** `[nums[i], nums[j], nums[k]]` such that:

* `i != j`, `i != k`, and `j != k`  
* `nums[i] + nums[j] + nums[k] == 0`  

The solution set must not contain duplicate triplets.

---

## Intuition

* Brute force would try all triplets → `O(n^3)`.  
* To optimize, we can **sort the array** and then fix one element.  
* For the remaining two numbers, use the **two-pointer approach** to find pairs that sum to the target (`-nums[i]`).  
* Sorting also helps skip **duplicates** efficiently.

---

## Two-Pointer Algorithm

1. Sort the array `nums`.  
2. Loop `i` from `0` to `n - 3`:  
   * Skip duplicates at `i`.  
   * Set `l = i + 1`, `r = n - 1`.  
   * While `l < r`:  
     * If `nums[i] + nums[l] + nums[r] == 0` → add triplet.  
       - Skip duplicates for `l` and `r`.  
       - Move both pointers.  
     * Else if sum < 0 → move `l++`.  
     * Else → move `r--`.  
3. Return all collected triplets.

**Why this works:**  
Sorting allows us to move pointers intelligently to increase or decrease the sum. Skipping duplicates ensures unique results.

---

## Complexity

* **Time:** `O(n^2)` — sorting `O(n log n)` + two-pointer scan for each element.  
* **Space:** `O(1)` extra (ignoring output).  

---

## Example

**Input:**  
nums = [-1, 0, 1, 2, -1, -4]

**Walkthrough:**  
* Sort → `[-4, -1, -1, 0, 1, 2]`  
* Fix `-4`: no valid pair.  
* Fix `-1`: pairs `(-1, 0, 1)` and `(-1, -1, 2)`.  
* Fix `0`: no new valid pair.  

**Output:**  
[[-1, -1, 2], [-1, 0, 1]]

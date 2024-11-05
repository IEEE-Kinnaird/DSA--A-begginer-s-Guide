# Searching Techniques 🔍🕵

## Introduction to Searching

In many competitive programming problems, we are required to find specific elements from an array or list. The way we search through this data can greatly impact the efficiency of our solution. In this article, we’ll cover two fundamental searching techniques:
- **Linear Search**
- **Binary Search**
We will also explore how to apply these techniques to common LeetCode problems and solve them one step by step.

---
## Linear Search
### What is Linear Search?
Linear search is the simplest method of searching through an array. It checks each element one by one until it finds the target element or reaches the end of the array.
### When to Use Linear Search
- When the array is **unsorted**.
- When we don’t care about the search efficiency (for small arrays).

### Time Complexity
- **Worst-case:** O(n), where n is the size of the array.

### Pseudocode for Linear Search


    LinearSearch(array, target):
    	for each element in array:
    		if element == target:
    			return index of element
    	return -1  # Target not found

---
## Binary Search
### What is Binary Search?
Binary search is an efficient algorithm used to find a target element in a sorted array. The idea is to divide the array into two halves repeatedly until the target is found.
### When to Use Binary Search
- When the array is **sorted**.
- When you need **faster search** in large datasets.

### Time Complexity
- **Worst-case:** O(log n), where n is the size of the array.

### Visualizing Binary Search
#### *Example:* Searching for 6 in a sorted array
Array: [1, 2, 3, 4, 5, 6, 7, 8, 9]
- **Step 1:** Low = 0, High = 8 → Mid = 4 → Array[4] = 5 *(target > 5)*
Shift low to mid + 1 → Low = 5
- **Step 2:** Low = 5, High = 8 → Mid = 6 → Array[6] = 7 *(target < 7)*
Shift high to mid - 1 → High = 5
- **Step 3:** Low = 5, High = 5 → Mid = 5 → Array[5] = 6 ***(target found)***

### Common Mistakes in Binary Search
- **Forget checking sorted arrays:** Binary search only works on sorted arrays. Ensure your array is sorted before applying the algorithm.
- **Handling edge cases:** Always check for edge cases like an empty array or an array with one element.
- **Off-by-one errors:** Be careful when updating low and high. An off-by-one error can cause the search to fail.

---
## **Sample Problems**

### 1. K-closest-elements

#### Binary Search for Starting Position:
- Define a search range with left = 0 and right = len(arr) - k. This ensures the final result has exactly k elements.
- Perform binary search within this range:
  - For each midpoint mid, compare the distance between x and arr[mid] with x and arr[mid + k].
  - If arr[mid + k] is closer to x, move the left bound up to mid + 1, narrowing the range to elements closer to x.
  - Otherwise, keep the right bound down to mid.

#### Select the k Closest Elements:
- Once left has settled on the best starting position, take the subarray arr[left:left + k] as the result. This subarray contains the k closest elements, already sorted.

---
### 2. Sqrtx

#### Define the Search Space:
- The integer square root of x will always be between 0 and x (for values of x ≥ 1).
- Set the initial range as low = 0 and high = x.

#### Binary Search to Find the Square Root:
- While low <= high:
  - Calculate the middle point: mid = (low + high) // 2.
  - Check if mid^2 is equal to x:
    - If mid^2 is exactly x, return mid as it’s the exact square root.
  - If mid^2 is less than x:
    - Move the search rightward by setting low = mid + 1. (Since mid might be our answer, but there could be a larger integer whose square is still <= x.)
    - Update a variable result = mid to store the current best candidate for the integer square root.
  - If mid^2 is greater than x:
    - Move the search leftward by setting high = mid - 1 (since mid is too large).

#### Return the Result:
- After the loop, the result will contain the largest integer y such that y2≤xy^2 \leq xy2≤x.

---
### 3. Search Insert Position

#### Initialize Pointers:
- Set left = 0 and right = len(nums) - 1 to cover the entire range of the array.

#### Binary Search:
- While left <= right:
  - Calculate the middle index: mid = (left + right) // 2.
  - Check the value at nums[mid]:
    - If nums[mid] == target: The target is found, so return mid.
    - If nums[mid] < target: Move the search to the right half by setting left = mid + 1.
    - If nums[mid] > target: Move the search to the left half by setting right = mid - 1.

#### Return Insert Position:
- If the target is not found in the array after the loop, left will point to the position where target should be inserted to maintain order.
- Return left as the insert position.

---



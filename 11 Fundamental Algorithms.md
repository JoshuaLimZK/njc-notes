#computing 
[[Computing]]

# 11 Fundamental Algorithms

# 11.1 Search Algorithms

> [!info] Search Algorithms
> Search Algorithms are used to retrieve information of some sort from a data structure.

## 11.1.1 Linear Search

A linear search searches for an item in a given array sequentially till the end of the collection or until it is found.

Look at each element in turn, comparing them with the value that you are looking for. Taken note of the index of the element once the value is found. You may also be required to report a special case if the element is not found.

**Basic Implementation in python:**
```python
# finds first instance of x in l

l = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
x = 4

for i in range(len(l)):
	if x == l(i):
		print(i)
		break
else:
	# the else case of a for loop only runs if the loop terminates without a break
	print(-1)
```

**Complexity of linear search** = $O(n)$

**Advantages:**
- Easy to implement
- Data does not need to be any particular order
**Disadvantages:**
- Very slow if value of $n$ is very large, inefficient when there is a lot of items
**Variations:**
- Find all instances of target
- Find particular instances of target (e.g. second, last)
- Find elements greater/smaller than target

## 11.1.2 Binary Search

If the array is in ascending order, we can make use of binary search to search for the element quickly.

**Procedure:**
1. Check the middle of the list
2. If it is the element we want, we can stop
3. If it is HIGHER than the value we want, repeat the search process with the portion of the list BEFORE the middle element
4. If it is LOWER than the value we want, repeat the search process with the portion of the list AFTER the middle element

![[Pasted image 20230916140231.png|500]]

**Iterative implementation in python:**
```python
# assuming list is already sorted
def iterBinary(l, x):
	start = 0 # tracks start index 
	end = len(l) - 1 # track end index
	
	while start <= end:
		mid = (start + end) // 2 # takes average of start and end indices
		if l[mid] == x:
			return mid
		elif l[mid] > x:
			end = mid - 1
		else:
			start = mid + 1
	return -1
```

**Recursive implementation in python:**
```python 
# assuming list is already sorted
def recBinary(l, x, start, end):
	mid = (start + end) // 2
	if start > end:
		return -1
	elif l[mid] == x:
		return mid
	elif l[mid] > x:
		return recBinary(l, x, start, mid - 1)
	else:
		return recBinary(l, x, mid + 1, end)
```

**Complexity of binary search** = $O(\log(n))$

**Advantages:**
- Faster than linear search
**Disadvantages:**
- Very slow if value of $n$ is very large, inefficient when there is a lot of items

# 11.2 Sorting Algorithms

> [!info] Sorting Algorithms
> Sorting Algorithms are used to sort data structures in a particular order

## 11.2.1 Insertion Sort

In the insertion sort algorithm, we compare each element, termed the `key` element with elements before it in the array. Then we insert the `key` element into its correct position in the array.

**Implementation in python:**
```python
def insertionSort(l):
	for i in range(1, len(l)):
		compare = i
		while compare > 0 and l[compare - 1] > l[compare]:
			l[compare], l[compare - 1] = l[compare - 1], l[compare]
			compare -= 1
	return l
```

**Average Case complexity of insertion sort** = $O(n^2)$
**Worst Case complexity of insertion sort** = $O(n^2)$

## 11.2.2 Bubble Sort

**Procedure:**
- In each iteration, take 2 consecutive elements and compare them.
* Swap the smaller value to the left and larger value to the right.
* Repeat until the larger elements "bubble up" to the end of the list, and the smaller elements moves to the "bottom".
* The right-hand side of the array is sorted.
* Repeat for the rest of the array

**Implementation in python:**
```python
def bubbleSort(a):
	for i in range(0,len(a)-1):
		swap = False
		for j in range(0,len(a)-i-1):
			if a[j] > a[j+1]:
				a[j], a[j+1] = a[j+1], a[j]
				swap = True
		if swap == False:
			break
	return a
```

**Average Case complexity of bubble sort** = $O(n^2)$
**Worst Case complexity of bubble sort** = $O(n^2)$

## 11.2.3 Quicksort

**Procedure:**
Quicksort is a sorting technique based on divide and conquer technique. Quicksort first selects an element, termed the `pivot`, and partitions the array around the pivot, putting every smaller element into a low array and every larger element into a high array.

- The `pivot` element can selected randomly, but one way to select the pivot is to use the element in the middle of the array as the pivot
- The first pass partitions data into 3 sub-arrays, `lesser` (less than pivot), `equal` (equal to pivot) and `greater` (greater than pivot).
* The process repeats for `lesser` array and `greater` array.

**Recursive Implementation in python:**
```python
import random
def recQuickSort(l):
	if l == []:
		return []
	pivot = l[random.randint(0, len(l) - 1)]
	equal = [i for i in l if i == pivot]
	lower = [i for i in l if i < pivot]
	higher = [i for i in l if i > pivot]

	return recQuickSort(lower)+equal+recQuickSort(higher)
```

The above solution for quicksort does not sort "in-place", ie. it creates new sub-arrays that uses up memory, so it is more space-complex. A solution that sorts in-place is as follows:
```python
def inplaceQuickSort(l, low, high):
	if low < high:
		pivot_index = partition(arr, low, high)
		
		inplaceQuickSort(l, low, pivot_index - 1)
		inplaceQuickSort(l, pivot_index + 1, high)

def partition(l, low, high):
	pivot = l[high]
	pivot_index = low

	for i in range(low, high):
		if l[i] < pivot:
		l[i], l[pivot_index] = l[pivot_index], l[i]
		pivot_index += 1

	l[pivot_index], l[high] = l[high], l[pivot_index]

	return pivot_index
```

**Average complexity for quicksort** = $O(n\log n)$
**Worst complexity for quicksort** = $O(n^2)$

## 11.2.4 Merge Sort

Similar to Quicksort, Merge sort is a sorting technique based on divide and conquer technique. It first divides the array into equal halves and then combines them in a sorted manner.

- if it is only one element in the list, it is already sorted. Return the list.
- divide the list recursively into two halves until it can no more be divided.
- merge the smaller lists into new list in sorted order.

**Recursive implementation in python:**
```python
def recMergeSort(l):
	mid = len(l) // 2
	left = l[:mid]
	right = l[mid:]

	recMergeSort(left)
	recMergeSort(right)

	merge(l, left, right)

def merge(l, left, right):
	i = j = k = 0

	while i < len(left) and k < len(right):
		if left[i] < right[j]:
			l[k] = left[i]
			i += 1
		else:
			l[k] = right[j]
			j += 1
		k += 1

	while i < len(left):
		l[i] = left[i]
		i += 1
		k += 1

	while i < len(right):
		l[i] = right[j]
		j += 1
		k += 1
```

**Average complexity for quicksort** = $O(n\log n)$
**Worst complexity for quicksort** = $O(n\log n)$

_Last edited 17/09/2023 by Joshua Lim NJC_
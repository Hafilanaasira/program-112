# program-112
import random

def partition(A, left_index, right_index):
    pivot = A[left_index]
    i = left_index + 1
    for j in range(left_index + 1, right_index):
        if A[j] < pivot:
            A[j], A[i] = A[i], A[j]
            i += 1
    A[left_index], A[i - 1] = A[i - 1], A[left_index]
    return i - 1

def quick_sort_random(A, left, right):
    if left < right:
        pivot = random.randint(left, right - 1)
        A[pivot], A[left] = A[left], A[pivot]  # Swap pivot with leftmost element
        pivot_index = partition(A, left, right)
        quick_sort_random(A, left, pivot_index)       # Left subarray
        quick_sort_random(A, pivot_index + 1, right)  # Right subarray

# Test examples
lists_to_sort = [
    [4, 3, 5, 1, 2],
    [5, 9, 10, 3, -4, 5, 178, 92, 46, -18, 0, 7],
    [1.1, 1, 0, -1, -1.1, 0.1],
    ['z','a','y','b','x','c']
]

for nums in lists_to_sort:
    print("\nOriginal list:")
    print(nums)
    quick_sort_random(nums, 0, len(nums))
    print("After applying Random Pivot Quick Sort:")
    print(nums)
output
Original list:
[4, 3, 5, 1, 2]
After applying Random Pivot Quick Sort:
[1, 2, 3, 4, 5]

Original list:
[5, 9, 10, 3, -4, 5, 178, 92, 46, -18, 0, 7]
After applying Random Pivot Quick Sort:
[-18, -4, 0, 3, 5, 5, 7, 9, 10, 46, 92, 178]

Original list:
[1.1, 1, 0, -1, -1.1, 0.1]
After applying Random Pivot Quick Sort:
[-1.1, -1, 0, 0.1, 1, 1.1]

Original list:
['z', 'a', 'y', 'b', 'x', 'c']
After applying Random Pivot Quick Sort:
['a', 'b', 'c', 'x', 'y', 'z']

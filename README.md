# 49.-Random-Pivot-Quick-Sort
import random

def partition(A, left, right):
    pivot = A[left]
    i = left + 1

    for j in range(left + 1, right):
        if A[j] < pivot:
            A[j], A[i] = A[i], A[j]
            i += 1

    A[left], A[i - 1] = A[i - 1], A[left]
    return i - 1

def quick_sort_random(A, left, right):
    if left < right:
        pivot = random.randint(left, right - 1)
        A[left], A[pivot] = A[pivot], A[left]
        pivot_index = partition(A, left, right)
        quick_sort_random(A, left, pivot_index)
        quick_sort_random(A, pivot_index + 1, right)

nums = [4, 3, 5, 1, 2]
print("Original list:", nums)
quick_sort_random(nums, 0, len(nums))
print("Sorted list:", nums)

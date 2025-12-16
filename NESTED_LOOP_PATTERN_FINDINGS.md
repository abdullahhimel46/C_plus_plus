# Nested Loop Pattern Usage Report

## Pattern Description
This report identifies all instances of the following nested loop pattern in the codebase:

```cpp
for (int i = 0; i < n - 1; i++) {
    for (int j = i + 1; j < n; j++) {
        // code here
    }
}
```

This pattern is commonly used for:
- Comparing all pairs of elements in an array
- Selection sort and bubble sort algorithms
- Finding triplets or combinations
- Avoiding duplicate comparisons (only compares each pair once)

## Files Using This Pattern

### 1. `array of objects - StudentMarkIDSorter`
**Location:** `/home/runner/work/C_plus_plus/C_plus_plus/array of objects - StudentMarkIDSorter`

**Lines:** 25-44

**Purpose:** Selection sort implementation for sorting Student objects

**Code Context:**
```cpp
for (int i = 0; i < n - 1; i++)
{
    for (int j = i + 1; j < n; j++)
    {
        //// Sorting students based on marks in descending order
        if (s[i].mark < s[j].mark) // Sort based on marks
        {
            swap(s[i], s[j]);
        }
        
        //// If marks are equal, sort based on the ID in ascending order
        if (s[i].mark == s[j].mark)
        {
            if (s[i].id > s[j].id)
            {
                swap(s[i], s[j]);
            }
        }
    }
}
```

**Algorithm:** Selection Sort with custom comparison (sorts by marks descending, then by ID ascending)

---

### 2. `tripletSumFinder`
**Location:** `/home/runner/work/C_plus_plus/C_plus_plus/tripletSumFinder`

**Lines:** 19-34

**Purpose:** Finding triplets that sum to a target value

**Code Context:**
```cpp
for (int i = 0; i < n - 2; i++)
{
    for (int j = i + 1; j < n - 1; j++)
    {
        for (int k = j + 1; k < n; k++)
        {
            if (a[i] + a[j] + a[k] == s)
            {
                flag = 1;
            }
        }
    }
}
```

**Algorithm:** Triple nested loop for finding three distinct indexed values that sum to target S
**Note:** This file has a triple nested loop pattern, which is an extension of the searched pattern

---

### 3. `Singly LikedList/ LinkedListSelectionSort` (Commented Out)
**Location:** `/home/runner/work/C_plus_plus/C_plus_plus/Singly LikedList/ LinkedListSelectionSort`

**Lines:** 83-96 (contains commented references to the pattern)

**Purpose:** Linked list selection sort (shows the pattern in comments for comparison with array version)

**Code Context:**
```cpp
for (Node *i = head; i->next != NULL; i = i->next)
//for(int i=0; i<n-1; i++)
{
    for (Node *j = i->next; j != NULL; j = j->next)
    //for(int j=i+1; j<n; j++)
    {
        if (i->data > j->data)
        //if(a[i]>a[j])
        {
            swap(i->data, j->data);
            //swap(a[i],a[j]);
        }
    }
}
```

**Algorithm:** Selection Sort adapted for linked lists, with commented array version showing the original pattern

---

## Summary

**Total Files Found:** 3

**Patterns Identified:**
1. **Selection Sort (Arrays):** 1 file - `array of objects - StudentMarkIDSorter`
2. **Triplet Sum Finding:** 1 file - `tripletSumFinder` (triple nested loop)
3. **Selection Sort (Linked Lists):** 1 file - `Singly LikedList/ LinkedListSelectionSort` (pattern shown in comments)

**Use Cases:**
- **Sorting algorithms:** Selection sort implementations
- **Combinatorial problems:** Finding triplets/pairs with specific properties
- **Comparison operations:** Comparing all pairs without duplicates

**Time Complexity:** O(n²) for the basic pattern, O(n³) for the triple nested variant

---

## Additional Notes

The pattern `for (int i = 0; i < n - 1; i++)` with `for (int j = i + 1; j < n; j++)` is characteristic of algorithms that need to:
- Compare each element with all elements after it
- Avoid comparing an element with itself
- Avoid duplicate comparisons (e.g., comparing i with j and then j with i)

This is more efficient than a simple double loop from 0 to n-1 for both indices, as it reduces the number of comparisons by approximately half.

---

**Report Generated:** 2025-12-16
**Repository:** abdullahhimel46/C_plus_plus

# EX 53 C program to remove duplicates in an array.
## DATE:
## AIM:
To write a C program to remove duplicates in an array.

## Algorithm
Implement various methods to remove duplicates from an array.

Compare algorithm efficiency and complexity.

Apply data structures like arrays and hash tables.

Analyze trade-offs in time and space.

Write modular and reusable code.

Observe performance on different inputs.

Strengthen skills for coding interviews.

## Program:
```
#include <stdio.h>

void printArray(int arr[], int size) {
    for(int i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

// 1. Naive method using nested loops (O(n^2))
int removeDuplicates_Naive(int arr[], int n) {
    int i, j, k;
    for(i = 0; i < n; i++) {
        for(j = i + 1; j < n; ) {
            if(arr[i] == arr[j]) {
                for(k = j; k < n - 1; k++)
                    arr[k] = arr[k + 1];
                n--;
            } else {
                j++;
            }
        }
    }
    return n;
}

// 2. Using auxiliary array (O(n^2) worst, better readability)
int removeDuplicates_AuxArray(int arr[], int n) {
    int temp[100], index = 0;
    for (int i = 0; i < n; i++) {
        int found = 0;
        for (int j = 0; j < index; j++) {
            if (arr[i] == temp[j]) {
                found = 1;
                break;
            }
        }
        if (!found)
            temp[index++] = arr[i];
    }
    for (int i = 0; i < index; i++)
        arr[i] = temp[i];
    return index;
}

// 3. Sort + remove duplicates (O(n log n))
#include <stdlib.h>
int compare(const void *a, const void *b) {
    return (*(int*)a - *(int*)b);
}
int removeDuplicates_Sorting(int arr[], int n) {
    qsort(arr, n, sizeof(int), compare);
    int index = 0;
    for (int i = 0; i < n; i++) {
        if (i == 0 || arr[i] != arr[i - 1])
            arr[index++] = arr[i];
    }
    return index;
}

// 4. Hashing with fixed-size map (O(n), works for small integers)
int removeDuplicates_Hashing(int arr[], int n) {
    int hash[1000] = {0};
    int index = 0;
    for (int i = 0; i < n; i++) {
        if (!hash[arr[i]]) {
            hash[arr[i]] = 1;
            arr[index++] = arr[i];
        }
    }
    return index;
}

// 5. Flag with visited marker (O(n^2), avoids shifting)
int removeDuplicates_Flag(int arr[], int n) {
    int flag[100] = {0}, index = 0;
    for (int i = 0; i < n; i++) {
        int seen = 0;
        for (int j = 0; j < index; j++) {
            if (arr[i] == arr[j]) {
                seen = 1;
                break;
            }
        }
        if (!seen)
            arr[index++] = arr[i];
    }
    return index;
}

// 6. Using a frequency array for positive integers
int removeDuplicates_Frequency(int arr[], int n) {
    int freq[1000] = {0}, index = 0;
    for (int i = 0; i < n; i++) {
        if (freq[arr[i]] == 0) {
            arr[index++] = arr[i];
            freq[arr[i]] = 1;
        }
    }
    return index;
}

// 7. Using a bit vector (limited range [0,31] only)
int removeDuplicates_BitVector(int arr[], int n) {
    unsigned int bitVector = 0;
    int index = 0;
    for (int i = 0; i < n; i++) {
        if (!(bitVector & (1 << arr[i]))) {
            bitVector |= (1 << arr[i]);
            arr[index++] = arr[i];
        }
    }
    return index;
}

int main() {
    int arr1[] = {1, 5, 2, 5, 2, 3, 1, 4};
    int n = sizeof(arr1)/sizeof(arr1[0]);

    int arr[100];

    printf("Original Array: ");
    printArray(arr1, n);

    // 1. Naive
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    int size = removeDuplicates_Naive(arr, n);
    printf("Naive method: ");
    printArray(arr, size);

    // 2. Auxiliary Array
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    size = removeDuplicates_AuxArray(arr, n);
    printf("Auxiliary Array: ");
    printArray(arr, size);

    // 3. Sorting
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    size = removeDuplicates_Sorting(arr, n);
    printf("Sorting method: ");
    printArray(arr, size);

    // 4. Hashing
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    size = removeDuplicates_Hashing(arr, n);
    printf("Hashing method: ");
    printArray(arr, size);

    // 5. Flag method
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    size = removeDuplicates_Flag(arr, n);
    printf("Flag method: ");
    printArray(arr, size);

    // 6. Frequency array
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    size = removeDuplicates_Frequency(arr, n);
    printf("Frequency array: ");
    printArray(arr, size);

    // 7. Bit Vector (works for values in range [0, 31])
    for(int i = 0; i < n; i++) arr[i] = arr1[i];
    size = removeDuplicates_BitVector(arr, n);
    printf("Bit vector method: ");
    printArray(arr, size);

    return 0;
}

```

## Output:
Original Array: 1 5 2 5 2 3 1 4 \
Naive method: 1 5 2 3 4 \
Auxiliary Array: 1 5 2 3 4 \
Sorting method: 1 2 3 4 5 \
Hashing method: 1 5 2 3 4 \
Flag method: 1 5 2 3 4 \
Frequency array: 1 5 2 3 4\ 
Bit vector method: 1 5 3 4 



## Result:
Thus the program was executed and the output was verified successfully.

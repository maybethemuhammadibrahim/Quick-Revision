# Cheat Sheet: Dynamic Memory Allocation (DMA) in C

Dynamic Memory Allocation allows programs to allocate and deallocate memory during runtime, enabling efficient memory usage. Here's everything you need to know for exams and practical applications.

---

### ## Key Functions

| **Function** | **Purpose**                            |
| ------------ | -------------------------------------- |
| `malloc`     | Allocates a specified number of bytes. |
| `calloc`     | Allocates and initializes an array.    |
| `realloc`    | Resizes previously allocated memory.   |
| `free`       | Deallocates allocated memory.          |

---

### ## Parameters for Each Function

#### **1. `malloc`**

```c
(cast type*) *malloc(size_t size);
```

- **Parameter**: `size` - Number of bytes to allocate.
- **Return Values**: 
	- Pointer to the allocated memory block if successful.
	- `NULL` if allocation fails.
- **Example**:

```c
int *arr = (int *)malloc(5 * sizeof(int)); // Allocates memory for 5 integers.
```

#### **2. `calloc`**

```c
(cast type*) *calloc(size_t num, size_t size);
```

- **Parameters**:
    - `num` - Number of elements.
    - `size` - Size of each element in bytes.
- **Return Values**: 
	- Pointer to the allocated and zero-initialized memory block if successful.
	- `NULL` if allocation fails.
- **Example**:

```c
int *arr = (int *)calloc(5, sizeof(int)); // Allocates memory for 5 integers and initializes to 0.
```

#### **3. `realloc`**

```c
(cast type*) *realloc(void *ptr, size_t size);
```

- **Parameters**:
    - `ptr` - Pointer to previously allocated memory.
    - `size` - New size in bytes.
- **Return Values**: 
	- Pointer to the allocated and zero-initialized memory block if successful.
	- `NULL` if allocation fails(original block remains unchanged)..
- **Example**:

```c
arr = (int *)realloc(arr, 10 * sizeof(int)); // Resizes array to hold 10 integers.
```

#### **4. `free`**

```c
void free(void *ptr);
```

- **Parameter**: `ptr` - Pointer to memory to deallocate.
- **Example**:

```c
free(arr); // Frees memory allocated to arr.
```

---

### ## Return Values for Each Function

- **`malloc`, `calloc`, `realloc`**:
    
    - Returns a pointer to the allocated memory on success.
    - Returns `NULL` if the allocation fails. Always check for `NULL` before using the pointer.
- **`free`**:
    
    - Does not return a value.

---

### ## Best Practices for Using DMA

1. **Always Check for `NULL`:**  
    Before using the pointer returned by `malloc`, `calloc`, or `realloc`, ensure it is not `NULL`.
    
    ```c
    if (ptr == NULL) {
        perror("Memory allocation failed");
        exit(EXIT_FAILURE);
    }
    ```
    
2. **Match `malloc`/`calloc` with `free`:**  
    For every memory allocation, ensure it is eventually freed to avoid memory leaks.
    
3. **Avoid Dangling Pointers:**  
    After freeing memory, set the pointer to `NULL`.
    
    ```c
    free(ptr);
    ptr = NULL;
    ```
    
4. **Use `sizeof`:**  
    Use `sizeof` to calculate memory size, as it is platform-independent.
    
    ```c
    int *arr = (int *)malloc(10 * sizeof(int));
    ```
    
5. **Prefer `calloc` for Arrays:**  
    Use `calloc` when you want zero-initialized memory for arrays.
    

---

### ## Guidelines on When to Free Memory

- Free memory **when it is no longer needed**.
- In functions, free memory before returning.
- For large applications, plan memory management to avoid both leaks and premature freeing.
- Use tools like Valgrind to detect memory leaks during testing.

---

### ## Tips and Tricks for Exam Preparation

1. **Memorize Function Signatures:**
    
    - Know the parameters and return types by heart.
2. **Understand Common Errors:**
    
    - Forgetting to check for `NULL`.
    - Accessing memory after `free`.
    - Mismatched memory allocation and deallocation.
3. **Practice Typical Questions:**
    
    - Write programs to dynamically allocate and resize arrays.
    - Implement functions that dynamically allocate memory for structs or matrices.
4. **Use Comments:**  
    Annotate your code to clarify allocation and deallocation points.
    
5. **Test Edge Cases:**
    
    - Allocate 0 bytes.
    - Reallocate to a smaller size.

---

### ## Sample Exam Program

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    // Allocate memory for 5 integers
    int *arr = (int *)malloc(5 * sizeof(int));
    if (arr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    // Initialize and print values
    for (int i = 0; i < 5; i++) {
        arr[i] = i + 1;
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Resize memory for 10 integers
    arr = (int *)realloc(arr, 10 * sizeof(int));
    if (arr == NULL) {
        printf("Memory reallocation failed\n");
        return 1;
    }

    // Initialize and print new values
    for (int i = 5; i < 10; i++) {
        arr[i] = i + 1;
    }
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Free memory
    free(arr);
    arr = NULL;

    return 0;
}
```

---

```C
#include <stdio.h>
#include <string.h>

int isPalindrome(char str[], int start, int end) {
    if (start >= end)
        return 1; // Base case: if we reach the middle
    if (str[start] != str[end])
        return 0; // Not a palindrome
    return isPalindrome(str, start + 1, end - 1); // Recursive call
}

int main() {
    char str[100];
    printf("Enter a string: ");
    scanf("%s", str);
    
    if (isPalindrome(str, 0, strlen(str) - 1))
        printf("The string is a palindrome.\n");
    else
        printf("The string is not a palindrome.\n");
    
    return 0;
}

```
---
```C
#include <stdio.h>
#include <string.h>

void reverseString(char str[], int start, int end) {
    if (start >= end)
        return; // Base case: stop when start crosses end
    char temp = str[start];
    str[start] = str[end];
    str[end] = temp;
    reverseString(str, start + 1, end - 1); // Recursive call
}

int main() {
    char str[100];
    printf("Enter a string: ");
    scanf("%s", str);
    
    reverseString(str, 0, strlen(str) - 1);
    printf("Reversed string: %s\n", str);
    
    return 0;
}

```
---
```C
#include <stdio.h>

void recursiveStrcpy(char *dest, const char *src) {
    if (*src == '\0') { // Base case: end of string
        *dest = '\0';
        return;
    }
    *dest = *src; // Copy current character
    recursiveStrcpy(dest + 1, src + 1); // Recursive call for the next character
}

int main() {
    char src[100], dest[100];
    printf("Enter source string: ");
    scanf("%s", src);
    
    recursiveStrcpy(dest, src);
    printf("Copied string: %s\n", dest);
    
    return 0;
}


```
---
```C
#include <stdio.h>

void recursiveStrcat(char *dest, const char *src) {
    if (*dest == '\0') { // Find the end of destination string
        if (*src == '\0') 
            return; // Base case: end of both strings
        *dest = *src; // Append character
        recursiveStrcat(dest + 1, src + 1); // Recursive call
    } else {
        recursiveStrcat(dest + 1, src); // Move to the end
    }
}

int main() {
    char dest[200], src[100];
    printf("Enter destination string: ");
    scanf("%s", dest);
    printf("Enter source string: ");
    scanf("%s", src);
    
    recursiveStrcat(dest, src);
    printf("Concatenated string: %s\n", dest);
    
    return 0;
}

```
---
```C
#include <stdio.h>

int main() {
    int arr[100], n, temp;

    // Input the size of the array
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    // Input the array elements
    printf("Enter %d elements:\n", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    // Bubble sort logic for ascending order
    for (int i = 0; i < n - 1; i++) { // Outer loop: passes
        for (int j = 0; j < n - i - 1; j++) { // Inner loop: compare adjacent elements
            if (arr[j] > arr[j + 1]) { // Swap if the current element is greater than the next
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    // Output the sorted array in ascending order
    printf("Array in ascending order:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}

```
---
```C
int fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

```
---

### **5. Pattern: Left Right Triangle**
```c
#include <stdio.h>

int main() {
    int rows;
    printf("Enter number of rows: ");
    scanf("%d", &rows);

    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    return 0;
}
```

---

### **6. Pattern: Right Right Triangle**
```c
#include <stdio.h>

int main() {
    int rows;
    printf("Enter number of rows: ");
    scanf("%d", &rows);

    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= rows - i; j++) {
            printf("  "); // Spaces for alignment
        }
        for (int k = 1; k <= i; k++) {
            printf("* ");
        }
        printf("\n");
    }

    return 0;
}
```

---

### **7. Pattern: Simple Triangle**
```c
#include <stdio.h>

int main() {
    int rows;
    printf("Enter number of rows: ");
    scanf("%d", &rows);

    for (int i = 1; i <= rows; i++) {
        for (int j = 1; j <= rows - i; j++) {
            printf(" "); // Spaces for alignment
        }
        for (int k = 1; k <= (2 * i - 1); k++) {
            printf("*");
        }
        printf("\n");
    }

    return 0;
}
```
---

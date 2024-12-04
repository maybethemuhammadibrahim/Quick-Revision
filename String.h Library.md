Here is a well-structured and concise guide to the functions in the `string.h` library with examples, tailored for exam preparation and easy pasting into Obsidian:

---

# `string.h` Library Functions in C

The `string.h` library provides functions for string manipulation, comparison, and memory handling. Below are some of its most useful functions, categorized and explained with examples.

---

### ## 1. `strlen`

#### **Purpose**

Calculates the length of a string (excluding the null character).

#### **Syntax**

```c
size_t strlen(const char *str);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Hello";
    printf("Length of '%s' is: %zu\n", str, strlen(str));
    return 0;
}
```

#### **Return Value**

- Returns the number of characters in the string, excluding the null character.

---

### ## 2. `strcpy` / `strncpy`

#### **Purpose**

Copies a source string into a destination string.

#### **Syntax**

```c
char *strcpy(char *dest, const char *src);
char *strncpy(char *dest, const char *src, size_t n);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char src[] = "Copy this!";
    char dest[20];
    strcpy(dest, src);
    printf("Copied string: %s\n", dest);
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the destination string (`dest`).

---

### ## 3. `strcat` / `strncat`

#### **Purpose**

Concatenates (appends) a source string to a destination string.

#### **Syntax**

```c
char *strcat(char *dest, const char *src);
char *strncat(char *dest, const char *src, size_t n);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char dest[50] = "Hello, ";
    char src[] = "World!";
    strcat(dest, src);
    printf("Concatenated string: %s\n", dest);
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the destination string (`dest`).

---

### ## 4. `strcmp` / `strncmp`

#### **Purpose**

Compares two strings.

#### **Syntax**

```c
int strcmp(const char *str1, const char *str2);
int strncmp(const char *str1, const char *str2, size_t n);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[] = "Hello";
    char str2[] = "World";
    int result = strcmp(str1, str2);
    if (result == 0) {
        printf("Strings are equal\n");
    } else if (result < 0) {
        printf("String1 is less than String2\n");
    } else {
        printf("String1 is greater than String2\n");
    }
    return 0;
}
```

#### **Return Value**

- `0`: Strings are equal.
- `< 0`: `str1` is lexicographically less than `str2`.
- `> 0`: `str1` is lexicographically greater than `str2`.

---

### ## 5. `strchr` / `strrchr`

#### **Purpose**

Finds the first or last occurrence of a character in a string.

#### **Syntax**

```c
char *strchr(const char *str, int c);
char *strrchr(const char *str, int c);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "example.com";
    char *pos = strchr(str, '.');
    if (pos) {
        printf("First occurrence of '.' found at position: %ld\n", pos - str);
    }
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the character if found.
- Returns `NULL` if the character is not found.

---

### ## 6. `strstr`

#### **Purpose**

Finds the first occurrence of a substring in a string.

#### **Syntax**

```c
char *strstr(const char *haystack, const char *needle);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Learn programming at LearnCode!";
    char *pos = strstr(str, "Learn");
    if (pos) {
        printf("Substring found: %s\n", pos);
    }
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the first occurrence of the substring.
- Returns `NULL` if the substring is not found.

---

### ## 7. `memcpy` / `memmove`

#### **Purpose**

Copies a block of memory from source to destination.

#### **Syntax**

```c
void *memcpy(void *dest, const void *src, size_t n);
void *memmove(void *dest, const void *src, size_t n);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char src[] = "Memory copy";
    char dest[20];
    memcpy(dest, src, strlen(src) + 1);
    printf("Copied memory: %s\n", dest);
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the destination (`dest`).

---

### ## 8. `strtok`

#### **Purpose**

Splits a string into tokens based on a delimiter.

#### **Syntax**

```c
char *strtok(char *str, const char *delim);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "one,two,three";
    char *token = strtok(str, ",");
    while (token) {
        printf("Token: %s\n", token);
        token = strtok(NULL, ",");
    }
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the next token or `NULL` when no tokens are left.

---

### ## 9. `memset`

#### **Purpose**

Fills a block of memory with a specified value.

#### **Syntax**

```c
void *memset(void *str, int c, size_t n);
```

#### **Example**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char buffer[20];
    memset(buffer, '*', 10);
    buffer[10] = '\0';
    printf("Buffer: %s\n", buffer);
    return 0;
}
```

#### **Return Value**

- Returns a pointer to the memory block (`str`).

---


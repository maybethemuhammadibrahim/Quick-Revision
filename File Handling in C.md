#### **Types of File Handling in C**

1. **Text Files** (`.txt`)
    
    - Data is stored in human-readable form.
    - Characters are stored as sequences of ASCII values.
    - Example: `Hello` is stored as `H e l l o`.
2. **Binary Files** (`.bin`)
    
    - Data is stored in a binary format (machine-readable).
    - Example: A number `123` is stored in binary form (`01111011`) rather than individual digits.

---

#### **Creating/Opening a File**

- **Key Functions**:
    
    1. **`fopen()`**: Opens an existing file or creates a new one.
    2. **`fclose()`**: Closes the file after use.
- **Syntax**:
    
    ```c
    FILE *fptr;
    fptr = fopen("C:\\program.txt", "w");
    if (fptr == NULL) {
        printf("Error opening file.\n");
        return 1;
    }
    fclose(fptr);
    ```
    

---

#### **File Opening Modes**

|**Mode**|**Description**|
|---|---|
|`"r"`|Opens a file for **reading**. Fails if the file does not exist.|
|`"w"`|Opens a file for **writing**. Creates a new file or truncates an existing file.|
|`"a"`|Opens a file for **appending**. Creates a new file if it doesn't exist.|
|`"r+"`|Opens a file for both **reading and writing**. Fails if the file does not exist.|
|`"w+"`|Opens a file for **reading and writing**. Creates a new file or truncates an existing file.|
|`"a+"`|Opens a file for **reading and appending**. Creates a new file if it doesn't exist.|
|`"rb"`|Opens a **binary file** for reading.|
|`"wb"`|Opens a **binary file** for writing.|

---

#### **Writing to a `.txt` File**

1. **`fputc()`**
    
    - Writes a single character to the file.
    - **Syntax**:
        
        ```c
        fputc(char, file_pointer);
        ```
        
    - **Parameters**:
        - `char`: Character to write.
        - `file_pointer`: Pointer to the file.
    - **Return Value**: The character written, or `EOF` on error.
    - **Example**:
        
        ```c
        FILE *fptr = fopen("C:\\output.txt", "w");
        fputc('A', fptr);
        fclose(fptr);
        ```
        
2. **`fputs()`**
    
    - Writes a string to the file.
    - **Syntax**:
        
        ```c
        fputs(string, file_pointer);
        ```
        
    - **Parameters**:
        - `string`: Null-terminated string to write.
        - `file_pointer`: Pointer to the file.
    - **Return Value**: Non-negative value on success, or `EOF` on error.
    - **Example**:
        
        ```c
        FILE *fptr = fopen("C:\\output.txt", "w");
        fputs("Hello, World!", fptr);
        fclose(fptr);
        ```
        
3. **`fprintf()`**
    
    - Writes formatted data to the file (like `printf`).
    - **Syntax**:
        
        ```c
        fprintf(file_pointer, "format_string", variable_list);
        ```
        
    - **Parameters**:
        - `file_pointer`: Pointer to the file.
        - `format_string`: Format specifier (e.g., `%d`, `%s`).
        - `variable_list`: Variables to format.
    - **Return Value**: The number of characters written, or negative value on error.
    - **Example**:
        
        ```c
        FILE *fptr = fopen("C:\\output.txt", "w");
        int num = 42;
        fprintf(fptr, "The answer is %d\n", num);
        fclose(fptr);
        ```
        

---
# .txt Files
---
#### **Reading from a `.txt` File**

1. **`fgetc()`**
    
    - Reads a single character from the file.
    - **Syntax**:
        
        ```c
        char ch = fgetc(file_pointer);
        ```
        
    - **Return Value**: The character read, or `EOF` on end-of-file or error.
    - **Usage in a Loop**:
        
        ```c
        FILE *fptr = fopen("C:\\input.txt", "r");
        char ch;
        while ((ch = fgetc(fptr)) != EOF) {
            putchar(ch);  // Print to console
        }
        fclose(fptr);
        ```
        
2. **`fgets()`**
    
    - Reads a line of text from the file.
    - **Syntax**:
        
        ```c
        fgets(buffer, count, file_pointer);
        ```
        
    - **Parameters**:
        - `buffer`: Character array to store the read line.
        - `count`: Maximum number of characters to read (including `\0`).
        - `file_pointer`: Pointer to the file.
    - **Example**:
        
        ```c
        char line[100];
        FILE *fptr = fopen("C:\\input.txt", "r");
        while (fgets(line, sizeof(line), fptr) != NULL) {
            printf("%s", line);
        }
        fclose(fptr);
        ```
        
3. **`fscanf()`**
    
    - Reads formatted data from the file.
    - **Syntax**:
        
        ```c
        fscanf(file_pointer, "format_string", variable_list);
        ```
        
    - **Parameters**:
        - `file_pointer`: Pointer to the file.
        - `format_string`: Format specifier.
        - `variable_list`: Variables to store the data.
    - **Example**:
        
        ```c
        FILE *fptr = fopen("C:\\input.txt", "r");
        int num;
        fscanf(fptr, "%d", &num);
        printf("Read number: %d\n", num);
        fclose(fptr);
        ```
        

---
# .dat files
---

#### **Writing to a `.dat` File**

`.dat` files are typically used to write structures or raw data. Use `fwrite()` to write binary data to the file.

1. **`fwrite()` Function**  
   - Writes binary data from memory to the file.  
   - **Syntax**:  
     ```c
     size_t fwrite(const void *ptr, size_t size, size_t count, FILE *stream);
     ```
   - **Parameters**:  
     - `ptr`: Pointer to the data to be written.  
     - `size`: Size of each element in bytes.  
     - `count`: Number of elements to write.  
     - `stream`: File pointer.  
   - **Return Value**: Number of elements successfully written.  

   - **Example**: Writing a structure to a `.dat` file.  
     ```c
     struct Student {
         int id;
         char name[50];
         float marks;
     };

     FILE *fptr = fopen("datafile.dat", "wb");
     if (fptr == NULL) {
         printf("Error opening file.\n");
         return 1;
     }

     struct Student s1 = {1, "John Doe", 85.5};
     fwrite(&s1, sizeof(s1), 1, fptr);  // Write one Student struct
     fclose(fptr);
     ```

---

#### **Reading from a `.dat` File**

Use `fread()` to read binary data back into memory.

1. **`fread()` Function**  
   - Reads binary data from the file into memory.  
   - **Syntax**:  
     ```c
     size_t fread(void *ptr, size_t size, size_t count, FILE *stream);
     ```
   - **Parameters**:  
     - `ptr`: Pointer to the memory where data will be stored.  
     - `size`: Size of each element in bytes.  
     - `count`: Number of elements to read.  
     - `stream`: File pointer.  
   - **Return Value**: Number of elements successfully read.  

   - **Example**: Reading a structure from a `.dat` file.  
     ```c
     struct Student {
         int id;
         char name[50];
         float marks;
     };

     FILE *fptr = fopen("datafile.dat", "rb");
     if (fptr == NULL) {
         printf("Error opening file.\n");
         return 1;
     }

     struct Student s1;
     fread(&s1, sizeof(s1), 1, fptr);  // Read one Student struct
     printf("ID: %d\nName: %s\nMarks: %.2f\n", s1.id, s1.name, s1.marks);
     fclose(fptr);
     ```

---

#### **Appending to a `.dat` File**

To add more records to a `.dat` file, open it in `"ab"` (append binary) mode.

- **Example**:  
  ```c
  struct Student {
      int id;
      char name[50];
      float marks;
  };

  FILE *fptr = fopen("datafile.dat", "ab");
  if (fptr == NULL) {
      printf("Error opening file.\n");
      return 1;
  }

  struct Student s2 = {2, "Jane Smith", 92.0};
  fwrite(&s2, sizeof(s2), 1, fptr);  // Append one Student struct
  fclose(fptr);
  ```

---

### **Common Functions for `.dat` Files**

| **Function** | **Purpose**                        | **Example Usage**                             |
|--------------|------------------------------------|-----------------------------------------------|
| `fwrite()`   | Write binary data to a file        | `fwrite(&data, sizeof(data), 1, fptr);`       |
| `fread()`    | Read binary data from a file       | `fread(&data, sizeof(data), 1, fptr);`        |
| `fseek()`    | Move file pointer to a specific location | `fseek(fptr, offset, SEEK_SET);`             |
| `ftell()`    | Get the current position of the file pointer | `long pos = ftell(fptr);`                   |

---
---
###  `fseek()` for `.txt` and `.dat` Files**

---

#### **Similarities**

1. **Purpose**:
    
    - `fseek()` moves the file pointer to a specified location in both `.txt` and `.dat` files.
2. **Syntax**:
    
    ```c
    int fseek(FILE *stream, long int offset, int origin);
    ```
    
    - **Parameters**:
        - `stream`: Pointer to the open file.
        - `offset`: Number of bytes to move.
        - `origin`: Reference point for the offset (`SEEK_SET`, `SEEK_CUR`, `SEEK_END`).
3. **Return Value**:
    - `0` on success.
    - Non-zero value on failure.
4. **Reference Points**:
    
    - `SEEK_SET`: Beginning of the file.
    - `SEEK_CUR`: Current file pointer position.
    - `SEEK_END`: End of the file.
5. **Usage Context**:
    
    - Both text and binary files use `fseek()` to navigate within the file.

---

#### **Differences Between `.txt` and `.dat` Files**

|**Aspect**|**Text Files (`.txt`)**|**Binary Files (`.dat`)**|
|---|---|---|
|**Unit of Movement**|Offset depends on the text encoding (e.g., newline handling).|Offset is always in bytes (no translation for encoding).|
|**Usage**|Mainly used for navigation by character position or line.|Commonly used for navigating by structure or record size.|
|**Complexity**|May require extra care for newline variations (e.g., `\n`, `\r`).|Easier and straightforward due to fixed byte offsets.|

---

#### **How to Use `fseek()`**

##### **For `.txt` Files**

- **Key Considerations**:
    
    - Offset is interpreted in terms of bytes but can be tricky due to newline variations (`\n`, `\r`).
- **Syntax**:
    
    ```c
    fseek(file_pointer, offset, SEEK_SET);
    ```
    
- **Example**: Moving to the 10th character in a `.txt` file. 
    
    ```c
    FILE *fptr = fopen("example.txt", "r");
    if (fptr == NULL) {
        printf("Error opening file.\n");
        return 1;
    }
    
    fseek(fptr, 10, SEEK_SET);  // Move to the 10th byte
    char ch = fgetc(fptr);      // Read the character
    printf("Character at position 10: %c\n", ch);
    fclose(fptr);
    ```
    

---

##### **For `.dat` Files**

- **Key Considerations**:
    
    - Offset is straightforward as it corresponds to byte positions directly, making it ideal for accessing specific records or structures.
- **Syntax**:
    
    ```c
    fseek(file_pointer, sizeof(record) * record_index, SEEK_SET);
    ```
    
- **Example**: Accessing the third record in a `.dat` file.
    
    ```c
    struct Record {
        int id;
        char name[50];
        float marks;
    };
    
    FILE *fptr = fopen("records.dat", "rb");
    if (fptr == NULL) {
        printf("Error opening file.\n");
        return 1;
    }
    
    struct Record rec;
    fseek(fptr, sizeof(rec) * 2, SEEK_SET);  // Move to the third record
    fread(&rec, sizeof(rec), 1, fptr);       // Read the record
    printf("ID: %d, Name: %s, Marks: %.2f\n", rec.id, rec.name, rec.marks);
    fclose(fptr);
    ```
    

---

#### **Key Differences in Practical Use**

|**Feature**|**Text Files (`.txt`)**|**Binary Files (`.dat`)**|
|---|---|---|
|**Purpose of Movement**|Navigate within characters/lines of text.|Direct access to structured records or byte positions.|
|**Newline Handling**|Care needed due to newline variations.|No newline considerations—bytes are raw.|
|**Use Cases**|Suitable for string manipulation or line-by-line access.|Ideal for working with fixed-size records like structs.|

---
```C
//Get file size 
fseek(file, 0, SEEK_END); 
long file_size = ftell(file); 
rewind(file);
```


#### **Practical Tips**

1. **Use `ftell()` for Debugging**:
    
    - Helps verify current file pointer position.
    - Example: `long pos = ftell(fptr);`
2. **Prefer Binary for Structured Data**:
    
    - Easier navigation with fixed offsets.
    - Example: `sizeof(structure)` helps calculate positions.
3. **Handle Text Offsets Carefully**:
    
    - Avoid assumptions about uniform character sizes in `.txt`.

By understanding these nuances, you can use `fseek()` effectively for both `.txt` and `.dat` file handling in C.
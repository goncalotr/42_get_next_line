      
# get_next_line - 42 File Descriptor Reader

This project contains the `get_next_line` function, which reads content line by line from a given file descriptor.

## Core Function

```c
char *get_next_line(int fd);
```
- Parameters: fd - The file descriptor to read from.
- Return Value:
  - Returns a string ending with \n (if the line had one).
  - Returns the final line without \n if EOF is reached before a newline.
  - Returns NULL if there is nothing left to read (EOF) or if an error occurred.

## Compilation

This function is typically compiled directly with the project that uses it.
Place get_next_line.c, get_next_line_utils.c (if used), and get_next_line.h in your project directory or include paths.
Define the buffer size using the BUFFER_SIZE flag during compilation. Example:

```c
# Compile your project, including the GNL source files
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 \
  your_main.c \
  get_next_line.c \
  get_next_line_utils.c \
  -o your_program
```

## Basic Usage

```c      
#include "get_next_line.h"
#include <fcntl.h> // For open
#include <stdio.h> // For printf
#include <stdlib.h> // For free

int main() {
    int fd;
    char *line;

    fd = open("your_file.txt", O_RDONLY);
    if (fd == -1) {
        // Handle error
        return (1);
    }
    while ((line = get_next_line(fd)) != NULL) {
        printf("%s", line);
        free(line); // Important: Free the allocated memory
    }
    close(fd);
    return (0);
}
```
   

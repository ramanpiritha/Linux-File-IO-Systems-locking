# Name: Piritharaman R
# Ref no: 212223230148

# Linux-File-IO-Systems-locking
Ex07-Linux File-IO Systems-locking
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## 1.To Write a C program that illustrates files copying 
```
#include <unistd.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h> // Include for debugging

int main() {
    char block[1024];
    int in, out;
    int nread;

    // Open input file
    in = open("filecopy.c", O_RDONLY);
    if (in == -1) {
        perror("Error opening input file");
        exit(1);
    }
    printf("Input file opened successfully\n");

    // Open or create output file
    out = open("file.out", O_WRONLY|O_CREAT, S_IRUSR|S_IWUSR);
    if (out == -1) {
        perror("Error opening/creating output file");
        exit(1);
    }
    printf("Output file opened/created successfully\n");

    // Read from input file and write to output file
    while ((nread = read(in, block, sizeof(block))) > 0) {
        printf("Read %d bytes from input file\n", nread);
        if (write(out, block, nread) != nread) {
            perror("Error writing to output file");
            exit(1);
        }
        printf("Wrote %d bytes to output file\n", nread);
    }

    if (nread == -1) {
        perror("Error reading from input file");
        exit(1);
    }

    printf("End of input file\n");

    // Close files
    close(in);
    close(out);

    printf("Files closed successfully\n");

    exit(0);
}
```
# OUTPUT:
![image](https://github.com/ramanpiritha/Linux-File-IO-Systems-locking/assets/147084116/058089f0-1a99-4939-926f-1060094c7120)

![image](https://github.com/ramanpiritha/Linux-File-IO-Systems-locking/assets/147084116/be254a43-33e2-4780-b455-be4c2b89c707)


# RESULT:
The programs are executed successfully.

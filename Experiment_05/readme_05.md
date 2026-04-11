
# Addressing Modes using GDB

##  Overview

This project demonstrates different **addressing modes in C programming** and analyzes them using the **GDB**.
It helps in understanding how data is accessed from memory, registers, and stack during program execution.

---

##  Aim

To implement and study various **addressing modes** in C and observe their behavior using the GNU Debugger (GDB).

---

##  Addressing Modes Covered

* Immediate Addressing
* Direct Addressing
* Register Addressing
* Indirect Addressing
* Register Indirect Addressing
* Indexed Addressing
* Base Register Addressing
* Relative Addressing
* Auto Increment
* Auto Decrement
* Stack Addressing

---

##  Code Implementation

```c
#include <stdio.h>

// Direct Addressing (global variable)
int global_var = 50;

void function_example() {
    int x = 5, y = 10;       // Stack Addressing

    int a = 20;              // Immediate Addressing
    int b = a;               // Register Direct

    int *p = &a;             // Indirect Addressing
    int c = *p;              // Register Indirect

    int arr[5] = {1,2,3,4,5}; // Indexed Addressing
    int d = arr[2];

    int *base = arr;         // Base Addressing
    int e = *(base + 3);

    for(int i = 0; i < 3; i++) { // Relative Addressing
        x += i;
    }

    int f = 0;               // Auto Increment
    f = arr[f++];

    int g = 2;               // Auto Decrement
    g = arr[--g];

    printf("%d %d %d %d %d %d %d\n", b, c, d, e, f, g, global_var);
}

int main() {
    function_example();
    return 0;
}
```

---

##  How to Run

###  Compile with Debug Symbols

```bash
gcc -g addressing.c -o addressing
```

### Run Program

```bash
./addressing
```

### Run with GDB

```bash
gdb ./addressing
```

---

## Useful GDB Commands

| Command           | Description          |
| ----------------- | -------------------- |
| `break main`      | Set breakpoint       |
| `run`             | Start execution      |
| `next`            | Execute line by line |
| `print variable`  | Show value           |
| `print &variable` | Show address         |
| `x address`       | Examine memory       |
| `info registers`  | View registers       |

---

## Learning Outcomes

* Understanding how **different addressing modes work**
* Visualizing memory and registers using **GDB**
* Gaining insight into **low-level execution of C programs**
* Learning how arrays, pointers, and loops access memory

---

##  Output Example

```
20 20 3 4 1 2 50
```

---

## Conclusion

This project successfully demonstrates various **addressing modes** in C.
Using **GDB**, we can clearly observe how data is accessed and manipulated at different memory levels, improving our understanding of system-level programming.

---


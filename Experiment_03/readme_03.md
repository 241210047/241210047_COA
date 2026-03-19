
# GDB Compiler

Objective : This lab foucuses on the compilation of the program using gdb compiler and helps in understand the core concept of Computer architecture and also the address indexing in the system this experiment helps us in understanding the following points.

* Basic GDB commands
* Compiling C code for Stack, Queue, Linked List using gdb

---

# 1. Compile Program with Debug Symbols
For ubuntu/Linux 
```bash 
gcc -g filename.c -o output
```


For Mac version>=M3/M4
```bash 
gcc -g -gdwarf-4 filename.c -o output
```

Example:

```bash
gcc -g stack.c -o stack
```

```bash
gcc -g -gdwarf-4 stack.c -o stack
```

---

# 2. Start GDB

```bash
gdb ./output
```

---

# 3. Important GDB Commands

| Command             | Description            |
| ------------------- | ---------------------- |
| break main          | Set breakpoint at main |
| break function_name | Break at function      |
| run                 | Start execution        |
| next                | Execute next line      |
| step                | Go inside function     |
| continue            | Continue execution     |
| print variable      | Print variable value   |
| info breakpoints    | Show breakpoints       |
| quit                | Exit GDB               |

---

# DEBUGGING FLOW

```text
Compile → Open GDB → Set Breakpoint → Run → Step → Observe Variables → Exit
```

---

# STACK IMPLEMENTATION

## Code (stack.c)

```c
#include <stdio.h>
#define SIZE 5

int stack[SIZE];
int top = -1;

void push(int value) {
    if (top == SIZE - 1) {
        printf("Overflow\n");
        return;
    }
    stack[++top] = value;
}

void pop() {
    if (top == -1) {
        printf("Underflow\n");
        return;
    }
    top--;
}

int main() {
    push(10);
    push(20);
    pop();
    return 0;
}
```

---

## GDB Flow for Stack

```bash
gdb ./stack
break main
run
next
step      # go inside push()
print top
print stack
continue
```

---

## Stack Flow

```text
PUSH → Add element → Increase top
POP  → Remove element → Decrease top
```

---

# QUEUE IMPLEMENTATION

## Code (queue.c)

```c
#include <stdio.h>
#define SIZE 5

int queue[SIZE];
int front = -1, rear = -1;

void enqueue(int value) {
    if (rear == SIZE - 1) {
        printf("Overflow\n");
        return;
    }
    if (front == -1) front = 0;
    queue[++rear] = value;
}

void dequeue() {
    if (front == -1 || front > rear) {
        printf("Underflow\n");
        return;
    }
    front++;
}

int main() {
    enqueue(1);
    enqueue(2);
    dequeue();
    return 0;
}
```

---

## GDB Flow for Queue

```bash
gdb ./queue
break main
run
step      # enter enqueue
print front
print rear
print queue
continue
```

---

## Queue Flow

```text
ENQUEUE → Insert at rear
DEQUEUE → Remove from front
FIFO (First In First Out)
```

---

# LINKED LIST IMPLEMENTATION

## Code (linkedlist.c)

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* head = NULL;

void insert(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = head;
    head = newNode;
}

void display() {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
}

int main() {
    insert(10);
    insert(20);
    display();
    return 0;
}
```

---

## GDB Flow for Linked List

```bash
gdb ./linkedlist
break main
run
step           # go inside insert
print head
print *head
next
continue
```

---

## Linked List Flow

```text
Create Node → Assign Data → Link Next → Update Head
```

---

# Summary

```text
GDB helps track:
✔ Variable values
✔ Function calls
✔ Memory changes
✔ Program flow
```

---

# End of README

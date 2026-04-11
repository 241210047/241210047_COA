
# Experiment 3 


## Objective

This lab foucuses on the compilation of the program using gdb compiler and helps in understand the core concept of Computer architecture and also the address indexing in the system this experiment helps us in understanding the following points.

* Basic GDB commands
* Compiling C code for Stack, Queue, Linked List using gdb

---


## Background Study

The **GNU Debugger (GDB)** is a powerful tool used to debug programs written in languages like C and C++. It allows programmers to:

* Execute programs line-by-line
* Set breakpoints to pause execution
* Inspect variable values and memory
* Trace function calls and logic flow

For debugging, programs must be compiled with the `-g` flag, which includes debugging symbols.

---

### Key Concepts

* **Breakpoint**: A point where execution stops for inspection
* **Step Execution**:

  * `next`: Executes next line
  * `step`: Enters function
* **Variable Inspection**:

  * `print variable` shows current value

---

### Data Structures Used

* **Stack (LIFO)**: Last In First Out
* **Queue (FIFO)**: First In First Out
* **Linked List**: Dynamic memory structure using pointers

GDB helps visualize how these structures behave internally by tracking variable changes like:

* `top` in stack
* `front/rear` in queue
* `head` pointer in linked list

---

# Setup

```bash
sudo apt update
sudo apt install build-essential gdb
```

---

### Verify Installation

```bash
gcc --version
gdb --version
```
# Compile Program with Debug Symbols
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

# Start GDB

```bash
gdb ./output
```

---

# Important GDB Commands

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


# RESULT

* Successfully compiled programs using:

  ```bash
  gcc -g -o test filename.c
  ```

* Executed programs inside GDB and:

  * Set breakpoints at `main()` and functions
  * Performed step-by-step execution
  * Observed real-time changes in variables

* Verified correctness of operations:

  * Stack → push and pop operations updated `top` correctly
  * Queue → enqueue and dequeue updated `front` and `rear`
  * Linked List → insertion correctly updated `head` pointer

* Debugging helped in:

  * Identifying logical errors
  * Understanding program flow clearly

---

# CONCLUSION

* GDB is an essential debugging tool for analyzing program behavior.

* It provides deep insights into:

  * Execution flow
  * Variable states
  * Memory handling

* Through this experiment:

  * We gained practical experience in debugging
  * Improved understanding of data structures
  * Learned how to detect and fix errors efficiently

* Overall, GDB enhances **program reliability and developer productivity** by enabling systematic debugging.

---

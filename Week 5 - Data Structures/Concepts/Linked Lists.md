
In recent weeks, you have learned about three useful primitives. A `struct`([[Structs]]) is a data type that you can define yourself. A `.` in __dot notation__ allows you to access variables inside that structure. The `*` operator is used to declare a pointer or dereference a variable.

Today, you are introduced to the **->** operator. It is an arrow. This operator **goes to an address** and **looks inside a structure**.

A __linked list__ is one of the most powerful 
**data structures**([[Data Structures]])within C. A linked list allows you to include values that are located in varying areas of memory. Further, they allow you to **dynamically grow and shrink the list as you desire**.

You might imagine three values stored in three different areas of memory as follows:
![Three boxes with 1 2 3 in separate areas of memory](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide036.png "three values in memory")

How could one stitch together these values in a list?
We could imagine the data pictured above as follows:
![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide037.png "three values in memory")

We could utilize more memory to keep track of where the next item using a pointer.
![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached where memory addresses are in those attached boxes](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide041.png "three values in memory")

Notice that NULL is utilized to indicate that nothing else is __next__
in the list.

By convention, we would keep one more element in memory, a pointer, that keeps track of the first item in the list, called the __head__ of the list.

![Three boxes with 1 2 3 in separate areas of memory with smaller boxes attached where memory addresses are in those attached boxes now with a final box with the memory address of the first box](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide042.png "three values in memory with pointer")

Abstracting away the memory addresses, the list would appear as follows:
![Three boxes with in separate areas of memory with smaller boxes with a final box where the one box points to another and another until the end of the boxes](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide043.png "three values in memory with pointer")

These boxes are called __nodes__. A __node__ contains both an **item** and a pointer called **next**. 

In code, you can imagine a node as follows:
```
    typedef struct node
    {
        int number;
        struct node *next;
    }
    node;
```

Notice that the item contained within this node is an integer called `number`. Second, a pointer to a node called `next` is included, which will point to another node somewhere in memory.

We can recreate `list.c` to utilize a linked list:
```
    // Start to build a linked list by prepending nodes
    
    #include <cs50.h>
    #include <stdio.h>
    #include <stdlib.h>
    
    typedef struct node
    {
        int number;
        struct node *next;
    } node;
    
    int main(void)
    {
        // Memory for numbers
        node *list = NULL;
    
        // Build list
        for (int i = 0; i < 3; i++)
        {
            // Allocate node for number
            node *n = malloc(sizeof(node));
            if (n == NULL)
            {
                return 1;
            }
            n->number = get_int("Number: ");
            n->next = NULL;
    
            // Prepend node to list
            n->next = list;
            list = n;
        }
        return 0;
    }
```

First, a `node` is defined as a `struct`. For each element of the list, memory for a `node` is allocated via `malloc` to the size of a node. `n->number` (or `n`’s number field) is assigned an integer. `n->next` (or `n`’s next field) is assigned `null`. Then, the node is placed at the start of the list at memory location `list`.

 Conceptually, we can imagine the process of creating a linked list. First, `node *list` is declared, but it is of a garbage value.
![One garbage value](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide055.png "linked list")

 Next, a node called `n` is allocated in memory.
![One garbage value called n with another pointer called list](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide059.png "linked list")

Next, the `number` of node is assigned the value `1`.
![n pointing to a node with 1 as the number and garbage value as the next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide064.png "linked list")

Next, the node’s `next` field is assigned `NULL`.
![n pointing to a node with 1 as the number and null as the value of next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide066.png "linked list")

Next, `list` is pointed at the memory location to where `n`points. `n` and `list` now point to the same place.
![n and list both pointing to a node with 1 as the number and null as the value of next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide068.png "linked list")

A new node is then created. Both the `number` and `next` field are filled with garbage values.
![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with garbage values](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide073.png "linked list")

 The `number` value of `n`’s node (the new node) is updated to `2`.
![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and garbage as the next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide075.png "linked list")

Also, the `next` field is updated as well.
![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and null as the next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide077.png "linked list")

Most importantly, we do not want to lose our connection to any of these nodes lest they be lost forever. 
Accordingly, `n`’s `next` field is pointed to the same memory location as `list`.    ![list pointing to a node with 1 as the number and null as the value of next and n pointing to a new node with 2 as the number and null as the next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide084.png "linked list")

Finally, `list` is updated to point at `n`. We now have a linked list of two items.    ![list pointing to a node with 1 as the number and next pointing to a node with an n pointing the same place the node with one points to a node with 2 as the number and null as the next](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide086.png "linked list")

Looking at our diagram of the list, we can see that the last number added is the first number that appears in the list. Accordingly, if we print the list in order, starting with the first node, the list will appear out of order.
We can print the list in the correct order as follows:

```
    // Print nodes in a linked list with a while loop
    
    #include <cs50.h>
    #include <stdio.h>
    #include <stdlib.h>
    
    typedef struct node
    {
        int number;
        struct node *next;
    } node;
    
    int main(void)
    {
        // Memory for numbers
        node *list = NULL;
    
        // Build list
        for (int i = 0; i < 3; i++)
        {
            // Allocate node for number
            node *n = malloc(sizeof(node));
            if (n == NULL)
            {
                return 1;
            }
            n->number = get_int("Number: ");
            n->next = NULL;
    
            // Prepend node to list
            n->next = list;
            list = n;
        }
    
        // Print numbers
        node *ptr = list;
        while (ptr != NULL)
        {
            printf("%i\n", ptr->number);
            ptr = ptr->next;
        }
        return 0;
    }
```

Notice that `node *ptr = list` creates a temporary variable that points at the same spot that `list` points to. The `while`prints what at the node `ptr` points to, and then updates `ptr` to point to the `next` node in the list.

In this example, inserting into the list is always in the order of **`O(1)`**, as it only takes a very small number of steps to insert at the front of a list.
Considering the amount of time required to search this list, it is in the order of **`O(n)`**, because in the worst case the entire list must always be searched to find an item. The time complexity for adding a new element to the list will depend on where that element is added. This is illustrated in the examples below.

Linked lists are not stored in a contiguous block of memory. They can grow as large as you wish, provided that enough system resources exist. The downside, however, is that more memory is required to keep track of the list instead of an array. For each element you must store not just the value of the element, but also a pointer to the next node. Further, linked lists cannot be indexed into like is possible in an array because we need to pass through the first **`n - 1`** elements to find the location of the **n**th element. Because of this, the list pictured above must be linearly searched. Binary search, therefore, is not possible in a list constructed as above.

Further, you could place numbers at the end of the list as illustrated in this code:
```
    // Appends numbers to a linked list
    
    #include <cs50.h>
    #include <stdio.h>
    #include <stdlib.h>
    
    typedef struct node
    {
        int number;
        struct node *next;
    } node;
    
    int main(void)
    {
        // Memory for numbers
        node *list = NULL;
    
        // Build list
        for (int i = 0; i < 3; i++)
        {
            // Allocate node for number
            node *n = malloc(sizeof(node));
            if (n == NULL)
            {
                return 1;
            }
            n->number = get_int("Number: ");
            n->next = NULL;
    
            // If list is empty
            if (list == NULL)
            {
                // This node is the whole list
                list = n;
            }
    
            // If list has numbers already
            else
            {
                // Iterate over nodes in list
                for (node *ptr = list; ptr != NULL; ptr = ptr->next)
                {
                    // If at end of list
                    if (ptr->next == NULL)
                    {
                        // Append node
                        ptr->next = n;
                        break;
                    }
                }
            }
        }
    
        // Print numbers
        for (node *ptr = list; ptr != NULL; ptr = ptr->next)
        {
            printf("%i\n", ptr->number);
        }
    
        // Free memory
        node *ptr = list;
        while (ptr != NULL)
        {
            node *next = ptr->next;
            free(ptr);
            ptr = next;
        }
        return 0;
    }
```

Notice how this code __walks down__ this list to find the end. When appending an element (adding to the end of the list) our code will run in **`O(n)`**, as we have to go through our entire list before we can add the final element. Further, notice that a temporary variable called `next` is used to track `ptr->next`.

Further, you could sort your list as items are added:
```
    // Implements a sorted linked list of numbers
    
    #include <cs50.h>
    #include <stdio.h>
    #include <stdlib.h>
    
    typedef struct node
    {
        int number;
        struct node *next;
    } node;
    
    int main(void)
    {
        // Memory for numbers
        node *list = NULL;
    
        // Build list
        for (int i = 0; i < 3; i++)
        {
            // Allocate node for number
            node *n = malloc(sizeof(node));
            if (n == NULL)
            {
                return 1;
            }
            n->number = get_int("Number: ");
            n->next = NULL;
    
            // If list is empty
            if (list == NULL)
            {
                list = n;
            }
    
            // If number belongs at beginning of list
            else if (n->number < list->number)
            {
                n->next = list;
                list = n; 
            }
    
            // If number belongs later in list
            else
            {
                // Iterate over nodes in list
                for (node *ptr = list; ptr != NULL; ptr = ptr->next)
                {
                    // If at end of list
                    if (ptr->next == NULL)
                    {
                        // Append node
                        ptr->next = n;
                        break;
                    }
    
                    // If in middle of list
                    if (n->number < ptr->next->number)
                    {
                        n->next = ptr->next;
                        ptr->next = n;
                        break;
                    }
                }
            }
        }
    
        // Print numbers
        for (node *ptr = list; ptr != NULL; ptr = ptr->next)
        {
            printf("%i\n", ptr->number);
        }
    
        // Free memory
        node *ptr = list;
        while (ptr != NULL)
        {
            node *next = ptr->next;
            free(ptr);
            ptr = next;
        }
        return 0;
    }
```

Notice how this list is sorted as it is built. To insert an element in this specific order, our code will still run in **`O(n)`** for each insertion, as in the worst case we will have to look through all current elements.

This code may seem complicated. However, notice that with pointers and the syntax above, we can stitch data together in different places in memory.



---

[[Algorithms#^big-o]]
[[Memory#^pointers]]

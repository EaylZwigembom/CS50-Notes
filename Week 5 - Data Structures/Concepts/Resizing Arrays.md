Rewinding to Week 2, we introduced you to your first data structure.

An array is a block of contiguous memory.
You might imagine an array as follows:
![three boxes with 1 2 3](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide019.png "array")

In memory, there are other values being stored by other programs, functions, and variables. Many of these may be unused garbage values that were utilized at one point but are available now for use.    ![three boxes with 1 2 3 among lots of other memory elements](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide022.png "array inside memory")

Imagine you wanted to store a fourth value `4` in our array. What would be needed is to allocate a new area of memory and move the old array to a new one? Initially, this new area of memory would be populated with garbage values.    ![Three boxes with 1 2 3 above four boxes with garbage values](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide025.png "two arrays with garbage values")

As values are added to this new area of memory, old garbage values would be overwritten.
![Three boxes with 1 2 3 above four boxes with 1 2 3 and a garbage value](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide026.png "two arrays with garbage value")

Eventually, all old garbage values would be overwritten with our new data.    ![Three boxes with 1 2 3 above four boxes with 1 2 3 4](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide027.png "two arrays with garbage value")

One of the drawbacks of this approach is that it’s bad design: Every time we add a number, we have to copy the array item by item.

Wouldn’t it be nice if we were able to put the `4` somewhere else in memory? By definition, this would no longer be an array because `4` would no longer be in contiguous memory. How could we connect different locations in memory?
In your terminal, type `code list.c` and write code as follows:

```
    // Implements a list of numbers with an array of fixed size
    
    #include <stdio.h>
    
    int main(void)
    {
        // List of size 3
        int list[3];
    
        // Initialize list with numbers
        list[0] = 1;
        list[1] = 2;
        list[2] = 3;
    
        // Print list
        for (int i = 0; i < 3; i++)
        {
            printf("%i\n", list[i]);
        }
    }
```

Notice that the above is very much like what we learned earlier in this course. Memory is preallocated for three items.

Building upon our knowledge obtained more recently, we can leverage our understanding of pointers to create a better design in this code. Modify your code as follows:
    
```
    // Implements a list of numbers with an array of dynamic size
    
    #include <stdio.h>
    #include <stdlib.h>
    
    int main(void)
    {
        // List of size 3
        int *list = malloc(3 * sizeof(int));
        if (list == NULL)
        {
            return 1;
        }
    
        // Initialize list of size 3 with numbers
        list[0] = 1;
        list[1] = 2;
        list[2] = 3;
    
        // List of size 4
        int *tmp = malloc(4 * sizeof(int));
        if (tmp == NULL)
        {
            free(list); // Free the first array
            return 1;
        }
    
        // Copy list of size 3 into list of size 4
        for (int i = 0; i < 3; i++)
        {
            tmp[i] = list[i];
        }
    
        // Add number to list of size 4
        tmp[3] = 4;
    
        // Free list of size 3
        free(list);
    
        // Remember list of size 4
        list = tmp;
    
        // Print list
        for (int i = 0; i < 4; i++)
        {
            printf("%i\n", list[i]);
        }
    
        // Free list
        free(list);
        return 0;
    }
```

Notice that a list of size three integers is created. Then, three memory addresses can be assigned the values `1`, `2`, and `3`. Then, a list of size four is created. Next, the list is copied from the first to the second. The value for the `4` is added to the `tmp` list. Since the block of memory that `list` points to is no longer used, it is freed using the command `free(list)`. Finally, the compiler is told to point `list` pointer now to the block of memory that `tmp` points to. The contents of `list` are printed and then freed. Further, notice the inclusion of `stdlib.h`.

It’s useful to think about `list` and `tmp` as both signs that point to a chunk of memory. As in the example above, `list`
at one point _pointed_ to an array of size 3. By the end, `list`was told to point to a chunk of memory of size 4. Technically, by the end of the above code, `tmp` and `list`
both pointed to the same block of memory.

One way by which we can copy the array without a for loop is by using `realloc`:
```
    // Implements a list of numbers with an array of dynamic size using realloc
    
    #include <stdio.h>
    #include <stdlib.h>
    
    int main(void)
    {
        // List of size 3
        int *list = malloc(3 * sizeof(int));
        if (list == NULL)
        {
            return 1;
        }
    
        // Initialize list of size 3 with numbers
        list[0] = 1;
        list[1] = 2;
        list[2] = 3;
    
        // Resize list to be of size 4
        int *tmp = realloc(list, 4 * sizeof(int));
        if (tmp == NULL)
        {
            free(list);
            return 1;
        }
        list = tmp;
    
        // Add number to list
        list[3] = 4;
    
        // Print list
        for (int i = 0; i < 4; i++)
        {
            printf("%i\n", list[i]);
        }
    
        // Free list
        free(list);
        return 0;
    }
```

Notice that the list is reallocated to a new array via `realloc`.
One may be tempted to allocate way more memory than required for the list, such as 30 items instead of the required 3 or 4. However, this is bad design as it taxes system resources when they are not potentially needed. Further, there is little guarantee that memory for more than 30 items will be needed eventually.
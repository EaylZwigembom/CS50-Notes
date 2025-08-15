Arrays offer contiguous memory that can be searched quickly. Arrays also offered the opportunity to engage in binary search.
Could we combine the best of both arrays and linked lists?
__Binary search trees__ are another data structure that can be used to store data more efficiently so that it can be searched and retrieved.

You can imagine a sorted sequence of numbers.    ![1 2 3 4 5 6 7 in boxes next to each other](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide118.png "tree")

Imagine then that the center value becomes the top of a tree. Those that are less than this value are placed to the left. Those values that are more than this value are to the right.
![1 2 3 4 5 6 7 in boxes arranged in a hierarchy 4 is at the top 3 and 5 are below that and 1 2 6 7 are below those](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide119.png "tree")

 Pointers can then be used to point to the correct location of each area of memory such that each of these nodes can be connected.
![1 2 3 4 5 6 7 in boxes arranged in a hierarchy 4 is at the top 3 and 5 are below that and 1 2 6 7 are below those arrows connect them in a tree formation](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide120.png "tree")

In code, this can be implemented as follows.
```
    // Implements a list of numbers as a binary search tree
    
    #include <stdio.h>
    #include <stdlib.h>
    
    // Represents a node
    typedef struct node
    {
        int number;
        struct node *left;
        struct node *right;
    }
    node;
    
    void free_tree(node *root);
    void print_tree(node *root);
    
    int main(void)
    {
        // Tree of size 0
        node *tree = NULL;
    
        // Add number to list
        node *n = malloc(sizeof(node));
        if (n == NULL)
        {
            return 1;
        }
        n->number = 2;
        n->left = NULL;
        n->right = NULL;
        tree = n;
    
        // Add number to list
        n = malloc(sizeof(node));
        if (n == NULL)
        {
            free_tree(tree);
            return 1;
        }
        n->number = 1;
        n->left = NULL;
        n->right = NULL;
        tree->left = n;
    
        // Add number to list
        n = malloc(sizeof(node));
        if (n == NULL)
        {
            free_tree(tree);
            return 1;
        }
        n->number = 3;
        n->left = NULL;
        n->right = NULL;
        tree->right = n;
    
        // Print tree
        print_tree(tree);
    
        // Free tree
        free_tree(tree);
        return 0;
    }
    
    void free_tree(node *root)
    {
        if (root == NULL)
        {
            return;
        }
        free_tree(root->left);
        free_tree(root->right);
        free(root);
    }
    
    void print_tree(node *root)
    {
        if (root == NULL)
        {
            return;
        }
        print_tree(root->left);
        printf("%i\n", root->number);
        print_tree(root->right);
    }
```

Notice this search function begins by going to the location of `tree`. Then, it uses recursion to search for `number`. The `free_tree` function recursively frees the tree. `print_tree` recursively prints the tree.

A tree like the above offers dynamism that an array does not offer. It can grow and shrink as we wish.
Further, this structure offers a search time of **O(log n)** when the tree is balanced.



---

[[Algorithms#^big-o]]

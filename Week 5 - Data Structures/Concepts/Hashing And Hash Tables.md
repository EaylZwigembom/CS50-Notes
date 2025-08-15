__Hashing__ is the idea of taking a value and being able to output a value that becomes a shortcut to it later.

For example, hashing __apple__ may hash as a value of `1`, and __berry__ may be hashed as `2`. Therefore, finding __apple__ is as easy as asking the __hash__ algorithm where __apple__ is stored. While not ideal in terms of design, ultimately, putting all __a__’s in one bucket and __b__’s in another, this concept of __bucketizing__ hashed values illustrates how you can use this concept: a hashed value can be used to shortcut finding such a value.

A __hash function__ is an algorithm that reduces a larger value to something small and predictable. Generally, this function takes in an item you wish to add to your hash table, and returns an integer representing the array index in which the item should be placed.

A __hash table__ is a fantastic combination of both arrays and linked lists. When implemented in code, a hash table is an __array__ of __pointers__ to __nodes__.

A hash table could be imagined as follows:
![a vertical column of 26 boxes one for each letter of the alphabet](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide157.png "alphabet")

Notice that this is an array that is assigned each value of the alphabet.
Then, at each location of the array, a linked list is used to track each value being stored there:    ![a vertical column of 26 boxes one for each letter of the alphabet with various names from the mario universe emerging to the right luigi is with l and mario is with m](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide169.png "alphabet")

__Collisions__ are when you add values to the hash table, and something already exists at the hashed location. In the above, collisions are simply appended to the end of the list.

Collisions can be reduced by better programming your hash table and hash algorithm. You can imagine an improvement upon the above as follows:
![a vertical column of various boxes arranged by L A K and L I N with Lakitu emerging from L A K and link emerging from L I N](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide184.png "alphabet")

Consider the following example of a hash algorithm:
![luigi being given to a hash algorithm outputting 11](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide173.png "hashing")

This could be implemented in code as follows:
```
    #include <ctype.h>
    
    unsigned int hash(const char *word)
    {
        return toupper(word[0]) - 'A';
    }
    
```

Notice how the hash function returns the value of `toupper(word[0]) - 'A'`.

You, as the programmer, have to make a decision about the advantages of using more memory to have a large hash table and potentially reducing search time or using less memory and potentially increasing search time.
This structure offers a search time of **O(n)**.




---

[[Algorithms#^big-o]]
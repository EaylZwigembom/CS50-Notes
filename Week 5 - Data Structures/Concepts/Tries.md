__Tries__ are another form of data structure. 
Tries are trees([[Trees]]) of arrays([[Arrays]]).
__Tries__ are always searchable in constant time.
One downside to __Tries__ is that they tend to take up a large amount of memory. Notice that we need $26 * 4 = 104$ `node`s just to store __Toad__!

__Toad__ would be stored as follows:        ![toad being spelled with one letter at a time where one letter is associated with one list T from one list O from another and so on](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide207.png "tries")

__Tom__ would then be stored as follows:    ![toad being spelled with one letter at a time where one letter is associated with one list T from one list O from another and so on and tom being spelled similarly where toad and tom share a two common letters T and O](https://cs50.harvard.edu/x/notes/5/cs50Week5Slide209.png "tries")

This structure offers a search time of **O(1)**.
The downside of this structure is how many resources are required to use it.



---
[[Algorithms#^big-o]]

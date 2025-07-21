A recursive algorithm is an algorithm that calls itself. Or to put more plainly in the world of C ,and frankly in the world of mathematics, a function is recursive if it calls itself.

An example of a recursive algorithm can be the phone book algorithm from week 0 ([[Algorithms#^Phone-Book]]):


```
1  Pick up phone book
2  Open the middle of phone book
3  Look at page
4  If person is on page
5       Call person
6  Else if person is earlier in book
7       Open middle of left half of book
8       Go back to line 3
9  Else if person is later in the book
10      Open middle of right half of book
11      Go back to line 3
12  Else
13      Quit
```

Here is a pseudocode of the phone book algorithm from week 0. You can see that in lines: 8, and 11 the code says to go back to line 3. That's a loop. But look at lines 7,8, and 10,11. Instead of saying open the whatever half of the book, and then go back to line 3, which really just means search that half. Why don't we just say that, so let's just say: search the left half of the book, and search the right half of the book:

```
1  Pick up phone book
2  Open the middle of phone book
3  Look at page
4  If person is on page
5       Call person
6  Else if person is earlier in book
		Search left half of book
9  Else if person is later in the book
		Search right half of book
12  Else
13      Quit
```

So now, instead of going back to line 3, the function can call itself and use the same logic for each half.

That's the recursive version of that algorithm and the algorithm before that is the loop (iterative) version.

So, sometimes you can solve problems with iteration(loops), and sometimes with recursion, and sometimes one problem is just better suited for on for the other. and in the coming weeks you will learn how to identify when you might want to use one technique or the other, but generally iteration tends to be the more comfortable approach.

Here is another example of iteration in context:

Let's say you want to print an height 4 pyramid out of hashes.

Well what's an height 4 pyramid?
It's just an height 3 pyramid but with one more layer.
Then what's an height 3 pyramid?
Well, it's actually an height 2 pyramid with one more layer.
Then what's an height 2 pyramid?
Well, it's an height 1 pyramid but with one more layer.
Then what's an height 1 pyramid?
It's just a single hash sign.

Check out the code snippets of week 3 to maybe understand a bit better what is a recursive algorithm and what is an iterative algorithm.

[Explanation Video](https://youtu.be/iCx3zwK8Ms8?t=6085)




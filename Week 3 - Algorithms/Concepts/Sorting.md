If you want to use search methods like Binary Search
([[Searching#^binary-search]]). You'll first need the dataset to be sorted in some way so that these search methods would actually work.

There are a couple of methods of sorting:

#### **Selection Sort**

Selection sort is a method of sorting that goes like that:

Let's say you have an array of numbers (0 through 7). but the position of each number in the array is random. So selection sort will sort the numbers like that:
First it goes through the list and finds the smallest number, then it swaps it with the number that is in the smallest index of the array(Only if that number isn't sorted), and then it finds the next smallest number and then it swaps it with the number that is in the next smallest index next to the number we sorted last time.

Here is an example of pseudocode for that sorting algorithm:

```
for i from 0 to n-1
	Find smallest number between numbers[i] and numbers[n-1]
	swap smallest number with numbers[i]
```

Note that this method finds the smallest number it found not by comparing it  to all of the items in the array but it compares it to the last smallest number it found; meaning the smallest number can first be 7, then 4, then 2, and maybe then 0.

[Explanation Video](https://youtu.be/iCx3zwK8Ms8)



#### **Bubble Sort**

Bubble sort is another sorting algorithm and it goes like that:

Let's say we have an array of numbers (o through 7) and each number is placed randomly in the array. bubble sort will sort these numbers like that:
It checks 2 numbers that are next to each other, if they are out of order, then it sorts ,them, then it goes to the next 2 numbers and does the same thing. and when it goes through all of the array and the array is still isn't sorted, then it goes over the same algorithm again and again until it is sorted. 

Here is an example of how one would write pseudocode for that sorting algorithm:

```
Repeat n-1 times
    For i from 0 to n-2
        If numbers[i] and numbers[i+1] out of order
            Swap them
    If no swaps
        Quit
```

Note that it's n-2 and not n-1 so when reaching the last index the algorithm won't go out of bounds.

[Explanation Video](https://youtu.be/iCx3zwK8Ms8?t=4105)
#### **Merge Sort**


We can now leverage recursion in our quest for a more efficient sort algorithm and implement what is called _merge sort_, a very efficient sort algorithm.
The pseudocode for merge sort is quite short:

```
If only one number
    Quit
Else
    Sort left half of number
    Sort right half of number
Merge sorted halves
```

Consider the following list of the numbers:

```
6341
```
First, merge sort asks, “is this one number?” The answer is “no,” so the algorithm continues.

```
6341
```
Second, merge sort will now split the numbers down the middle (or as close as it can get) and sort the left half of numbers.

```
63|41
```

Third, merge sort would look at these numbers on the left and ask, “is this one number?” Since the answer is no, it would then split the numbers on the left down the middle.

```
6|3
```
Fourth, merge sort will again ask, “is this one number?” The answer is yes this time! Therefore, it will quit this task and return to the last task it was running at this point:

```
63|41
```
Fifth, merge sort will sort the numbers on the left.

```
36|41
```
Now, we return to where we left off in the pseudocode now that the left side has been sorted. A similar process of steps 3-5 will occur with the right-hand numbers. This will result in:

```
36|14
```
 Both halves are now sorted. Finally, the algorithm will merge both sides. It will look at the first number on the left and the first number on the right. It will put the smaller number first, then the second smallest. The algorithm will repeat this for all numbers, resulting in:

```
1346
```
Merge sort is complete, and the program quits.
Merge sort is a very efficient sort algorithm.

[Explanation Video](https://youtu.be/iCx3zwK8Ms8?t=6916)

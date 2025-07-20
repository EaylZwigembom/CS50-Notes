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
#### **Merge Sort**


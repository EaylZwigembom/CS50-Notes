Searching is a problem in computer science and that problem is baisically finding information efficiently.

![[Pasted image 20250616062954.png]]

The input is some kind of an array or a variable that there is a piece of data inside it that needs to be found and the output is a bool: yes the data is in that place or no that data is not in that place. And between both of the input and output there's an algorithm 

![[Pasted image 20250720104609.png]]

Because a computer can't look at all of its data slots and find the piece of data it needs it some kind of a way to look for the data. One of the ways is:

#### **Linear Search**
^linear-search

Linear searching is basically just meaning that the computer goes through each slot of data it has in an array until it finds the piece of data it wants. Let's take a look at this array of numbers:

![[Pasted image 20250720105101.png]]

Let's say the computer's objective is to find the number 50. Well becasue the computer can't just look at the entire of the array and just go to the slot where 0 is, it has to go through each slot until it find the number 50. Let's 
![[Pasted image 20250720105219.png]]

You can see that array as a row of closed doors. The computer has to go through each one and check if the number 50 is there, If it's there then the computer can stop searching and if it's not there, the computer will go on to the next door until until it finds the number 50.

Here is a pseudocode example for that algorithm:
```
For each door from left to right

    If 50 is behind door

        Return true

Return false
```
Now you might see that the return false is not in the conditional, and that's because if it were inside of the condition if on the first step the computer didn't find the 50 it would just return false and the program would end

Well even though that searching method is ok for small datasets, it would take a lot of time to large data sets with millions of data. Because the computer will have to go through each of those millions until it has to find that tiny piece of information. Well there's a better approach for finding data and that is binary search

#### **Binary Search**
^binary-search

Binary search is another way of searching for data and it's a lot more efficient than linear searching. 

What binary searching means is just going to the middle of the dataset, then checking if that piece of information is to the left of where your at or to the right of where you're at. then you go to that direction and with one simple step you've already eliminated half of the problem. 

Let's talk again about the phone book problem from week 0 
([[Algorithms#^Phone-Book]])

Let's say that phone book has 1000 pages, if we use binary searching, just from the first step of the algorithm we go to 500 pages, then to 250 pages, and so fourth until we reach only 1 page. and let's say a year after the number of pages has been doubled to 2000 pages. We would only need one extra step and then we get to where we were before the number of pages has doubled

Here is a pseudocode example for that algorithm:
```
If no doors left
    Return false
If 50 is behind middle door
    Return true
Else if 50 < middle door
    Search left half
Else if 50 > middle door
    Search right half
```
Notice that the code also checks if there are no doors left and if so that means that the piece of data that the computer was looking for isn't even in the dataset and if we are not preparing for all of the scenarios that can happen, that's when the computer can crash


### **Running Time**
^big-O

Go to [[Algorithms#^big-o]]

Here is an addition to there:

|Notation|Name|What It Tells You|Analogy / Notes|
|---|---|---|---|
|**O(n)**|Big-O (Upper Bound)|_Worst-case_ performance|“At most this bad”|
|**Ω(n)**|Omega (Lower Bound)|_Best-case_ performance|“At least this fast”|
|**Θ(n)**|Theta (Tight Bound)|_Exact_ performance (best = worst = same)|“Always takes this time” (when equal)|

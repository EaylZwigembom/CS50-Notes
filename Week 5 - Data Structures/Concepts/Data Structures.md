
**Data structures** essentially are forms of organization in memory. There are many ways to organize data in memory.

**Abstract data types** are ways of organizing information that we can conceptually imagine, but don't necessarily need to know how to implement them in code because there are many different ways of implementing them. 
When learning about computer science, it’s often useful to begin with these conceptual data structures. 
Learning these will make it easier later to understand how to implement more concrete data structures.

#### **Queues**

^af2255

Queues like in real life are lines . In real life it can be a line of people waiting to enter the movie theater or a line of people waiting to ride the roller coaster. In any kind of line in the real world we have queues. Queues have some kind of ordering, often of people. 

So a queue or a line in thee real world as we know it is actually an example of a **FIFO** data type which means: 
**F**irst **I**n **F**irst **O**ut.

So that's a **property** of this structure, no matter how you implement it, that describes sort of the equity of how you put the data in and get it out.

If you want to implement the queue data structure in code where you want to ensure a **FIFO** property, you would generally have two functions or two fundamental operations:

**`enqueue`** - putting data **into** the queue.

**`dequeue`** - take data **out of** the queue.

And just as **FIFO** implies, the **first in**, is the first one to be **enqueued** but they're also the first one **out** to be **dequeued**.

Here's an example on how to make this in code:
```
const int CAPACITY = 50;

typedef struct
{
	person people[CAPACITY];
	int size;
} queue;
```

let's say that you want to have a queue, like a line that can fit **50** people in total, we can declare an **`int`** and make it **`const`** so it can't actually change and initialize that to **50**. And then we could use that elsewhere in our code. Then we can create our own structure([[Structs]]) using **`typedef struct`** that includes an array of type person(recall from [[Structs]]) that the **max size** of the array will be the const int we initialized before. Then we add an int that keeps track of the **size** of the queue. 
The **size** and **capacity** mean two things very distinct:

The **capacity** is and always will be 50 because it's a **`const`**.

But the **size** is going to be the **current number of people** in the queue, and it stands to reason that you've get to keep track of both because otherwise you might have 50 **garbage values** in the memory, if you want to keep track of how many of those are **valid** and represent in this case people, you need to know if there's 0 people there or 49 or 50 or anywhere in between

So this is how we might in C code implement the idea of a queue using familiar syntax by kind of layering some of these ideas we've seen already.



But you don't always want queues and you specifically don't always want **FIFO**s, so there also exist in the world these things called stacks.
#### **Stacks**

^6ed3d2

Let's say I have **`14`** shirts, I wear a different shirt **each day** and I do laundry **once a week**. if I **stack** those shirts on top of each other than each day I use the shirt that is on top of the stack. but if I do laundry **once a week** that means that in every end of the week I'll put the **`7`** shirts I wore that week again on top of the stack, and it would go like that forever. that means I'll never even wear the other **`7`** shirts bellow the **`7`** shirts I use each week. 

the **stack** data structure(like in the demonstration above) is an example of the **LIFO** data type.
**LIFO** means: **L**ast **I**n **F**irst **O**ut.

If you want to implement the stack data structure in code where you want to ensure a **LIFO** property, you would generally have two functions or two fundamental operations:

**`push`** - push data on **top** of the stack.

**`pop`** - remove data from the **top** of the stack.

In code we could implement the stack and the queues pretty much the same:
```
const int CAPACITY = 50;

typedef struct
{
	person people[CAPACITY];
	int size;
} stack;
```

Notice that the only difference here is the name of the structure. The difference in code between queues and stacks is how we **operate** with them. you would probably removing and adding data to the stack from a different part of the array than you would from a queue. Here is an example on adding data from a queue and adding data to a stack. In stack you might want to remove the data from the end of the array(starting from size) instead of the start(index 0).

Here's an example of adding and removing data from a stack and a queue
```
#include <stdio.h>
#inlude <cs50.h>

const int CAPACITY = 50;

typedef struct
{
	person people[CAPACITY];
	int size;
} queue;

const int CAPACITY = 50;

typedef struct
{
	person people[CAPACITY];
	int size;
} stack;

queue people;
stack people;

void AddData(char *name, int age, int index);
void RemoveData();

int main(void)	
{
	char *name;
	int age = 0;
	int size = get_int("Num of people: ");
	for (int i = 0; i < size)
	{
		name  = get_string("name: ");
		age  = get_string("age: ");
		AddData(name, age, i);
	}
	RemoveData();
	
}
void AddData(char *name, int age, int index)
{
	// Add to queue
	queue.people[i].people.name = name;
	queue.people[i].age = age;
	queue.size++;
	
	// Add to stack
	stack.people[i].name = name
	stack.people[i].age = age;
	stack.size++;
}

void RemoveData()
{
	// Remove from queue
	for (int i = 0; i < queue.size; i++)
	{
		Remove(queue.people[i]);
	}
	// Remove from stack
	for (int i = stack.size; i > 0; i--)
	{
		Remove(stack.people[i]);
	}
}

void Remove(person person)
{
	// code that removes said person
}

```



#### **Jack Learns he Facts**

We watched a video called [Jack Learns the Facts](https://www.youtube.com/watch?v=ItAG3s6KIEI) by Professor Shannon Duvall of Elon University.
the [original video](https://www.youtube.com/watch?v=zmrdfd0eRYQ)

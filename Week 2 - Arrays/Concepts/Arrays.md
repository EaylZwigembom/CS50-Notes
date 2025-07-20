#C #Arrays

An **array** is a **==sequence of values==**.

In C an array would look like that: ^utilize
```
type variable_name[numberOfPlaces];
```

when you want to store a value in one of the places of the array you do something like that:
```
variable_name[desiredPlace] = {value};
```

It's important to note that the value you store in the array has to be **within its indexes**. for example: ^interact
```
int numbers[2];
numbers[5] = 3;
```
This kind of action would result in an error because there is no index 5 in that array, the only indexes available in that array are: **0, and 1.**

Another way that you can initialize an array
```
int numbers[] = {20, 500, 10, 5, 100, 1, 50};
```
If you want to create an array that has specific values its just an easier way to do that.

You can think of arrays as some kind of lists, for example: A list of the scores you got this semester were : 73. 72, and 33. So the list is scores and the values are 73, 72 and 33. 

In C it would look something like that:

```
int scores[3];
scores[0] = 73;
scores[1] = 72;
scores[2] = 33;
```

Now, let's say there is a function that you want to **cast** a certain array to. **==If you'll need to know what is he length of that array==**, **you have to specify it in the function**, because the function wouldn't know it by itself.
Here is an example:

```
#include <stdio.h>

void Length(int scores[]);

int main(void)

{

    int scores[3];
    scores[0] = 72;
    scores[1] = 73;
    scores[2] = 33;

    Length(scores);

}

void Length(int scores[])
{
    int length = sizeof(scores);
    print(length);
}
```

This code wouldn't work because C will store only the values of the array. So here's what we need to do in order to make the code work:

```
#include <stdio.h>

void Length(int scores[]);

int main(void)

{

    int scores[3];
    scores[0] = 72;
    scores[1] = 73;
    scores[2] = 33;

    Length(scores, sizeof(scores));

}

void Length(int scores[], int length)
{
    print(length);
}
```

Remember that you will need to do that only if you need the function to know what is the length of that array.


If your array is **an array of arrays**, for example: an array of **strings**([[Strings]]). and you want to ==**access some point in the array that is stored in some index of the main array==** you can do it like this:

```
int main(void)
{
	string words[1];
	words[0] = "HI!";
	
	printf("%c%c\n", words[0][0], words[0][1]);
}
```

The output would be this:

```
HI
```

So the **first bracket** is the index in the **main array** and the **second bracket** is the index in the **array that is stored inside that index of the array**
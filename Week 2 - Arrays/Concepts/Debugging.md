#C #Debugging
#Debug

**Debugging** is a term referred to **==fix bugs in your code==**. 
a bug is a **mistake in your code**, it can be a problem in the **syntax** or logic, **and** it can be just that the **program won't do what you want it to do**.

Here are examples for the 2 types of bugs:

##### Syntax
```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	string name = get_string("Whatt's your name? ");
	print("Hello, %s\n", name);
}
```
Here, there is a program that prompts the user for it's name and then prints it. But there is an error, a **syntax** error: **==there is no such function as print()==** **==in the C language==**. If you want the program to work you need to change it to **printf()**.


##### Program Won't Do What You Want It To


```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	for (int i = 0; i <= 3; 1++)
	{
		printf("#\n");
	}
}
```
Here there is a program that is supposed to print a tower composed of **three** hashes (#). **==The program is correct==**, it has no errors. But, there is a bug. Here is the output of the program:

```
clang -o buggy buggy.c -lcs50
./buggy
#
#
#
#
```

The program was supposed to print **three** hashes but it printed **four**. 
Let's now debug this code by printing the value of i also:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	for (int i = 0; i <= 3; 1++)
	{
		printf("i is: %i\n", i);
		printf("#\n");
	}
}
```
Here is the the output of this program:

```
clang -o buggy buggy.c -lcs50
./buggy
i is: 0
#
i is: 1
#
i is: 2
#
i is: 3
#
```
You can see that you get the fourth hash when **==i is: 3==**. Let's get back to the original code for a moment and continue from there:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	for (int i = 0; i <= 3; 1++)
	{
		printf("#\n");
	}
}
```
So now if the fourth hash is printed when **==i is 3==**, then you can change in the loop **`i <= 3`** to **`i < 3`** and then the problem would be fixed.


##### **IMPORTANT NOTE**
Do this type of debugging only at your computer, **==don't submit the code with that because it might confuse the auto grader==**.

Use **==debug50==** for debugging more efficiently.
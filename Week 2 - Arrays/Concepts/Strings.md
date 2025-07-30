#C #Strings

A string is a sequence of characters stored in a variable. In C there is not really a type called string([[Memory#^strings]]), so to make strings you use arrays of chars:

```
#include <stdio.h>

int main(void)
{
	char s[3];
	s[0] = 'H';
	s[1] = 'I';
	s[2] = '!';

	printf("%c%c%c\n", s[0], s[1], s[2]);
}


---------------------------------------------------------------
make hi
./hi
HI!
$
```

![[Pasted image 20250716151906.png]]
This is how the string would look in the computer's memory

It turns out that because characters are actually just numbers([[ASCII]]), we can tell the computer to treat the chars as integers, so let's do that and see what will we see:

```
#include <stdio.h>

int main(void)
{
	char s[3];
	s[0] = 'H';
	s[1] = 'I';
	s[2] = '!';

	printf("%i %i %i\n", s[0], s[1], s[2]);
}


---------------------------------------------------------------
make hi
./hi
72 73 33
$
```

We would get the numbers that represents each character.

But how does the computer knows where the variable starts and where the variable ends. Because the variable is actually contained in multiple slots of memory. Why when I use s as a placeholder and print it why won't the program print everything in the computer's memory?

So it turns out that the way a computer keeps track of where the end of a string is, even if that string is three characters, the length of the string, the length of the array really that's storing the string, is technically 4. It's 1 plus whatever the actual length of the phrase is. The 1 plus slot is a kind of a marker that tells the computer: The string ends there. And that slot is filled with all zeros
![[Pasted image 20250716152000.png]]
Which is actually just 0
![[Pasted image 20250716152010.png]]

Now let's see what happens when we call `s[3]` in the program:

```
#include <stdio.h>

int main(void)
{
	char s[3];
	s[0] = 'H';
	s[1] = 'I';
	s[2] = '!';

	printf("%i %i %i %i\n", s[0], s[1], s[2], s[3]);
}


---------------------------------------------------------------
make hi
./hi
72 73 33 0
$
```


That 0 is called `NUL` which is just a sentinel special character that is basically saying: the string ends there

More about chars here:
[[ASCII#^chars]]


Also, in C. You can't compare strings so use the function **`strcmp()`** from the **`string.h`** header file
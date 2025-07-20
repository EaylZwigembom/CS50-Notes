#Command-Line-Arguments #C 

In C in the main function you can write instead of void in the brackets you can write:

```
#include <stdio.h>

int main(int argc, string argv[])
{

}
```

And it would enable you to make command line arguments in your program.

`int argc`: This variable is counting how many command line arguments there are.

`string argv[]`: This is an array containing all of the command line arguments.

Let's try to make a program with out new found knowledge

```
#include <stdio.h>
#include <cs50.h>

int main(int argc, string argv[])
{
	printf("Hello, %s\n", argv[0]);
}

---------------------------------------------------------------
TERMINAL

./greet Eyal
Hello, ./greet
```

This program is supposed to greet the user. When running the program in the terminal the user inputs their name and then the program is supposed to greet them. But what the program did is just write ./greet (The function to run the program). That's because that also counts as an argument. so let's fix that:

```
#include <stdio.h>
#include <cs50.h>

int main(int argc, string argv[])
{
	printf("Hello, %s\n", argv[1]);
}

---------------------------------------------------------------
TERMINAL

./greet Eyal
Hello, Eyal
```

Here is my program that I did with command line arguments, try to understand what I did there:

```
#include <cs50.h>
#include <stdio.h>

int main(int argc, string argv[])
{
    if (argc > 1)
    {
        printf("Hello, ");
        for (int i = 1; i < argc; i++)
        {
            printf("%s ", argv[i]);
        }
        printf("\n");
    }
    else
    {
        printf("Usage:\n");

        printf("./greet <name>\n");
    }
}
```
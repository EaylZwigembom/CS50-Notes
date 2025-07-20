In C, a data structure is a container that can contain multiple types of data.

Here's how to create on in C:
```
typedef struct
{
	// Here you put the variables you want
}
name;
```

Here is an example of a data structure that contains peoples name and age:

```
typedef struct
{
	string name;
	int age;
}
person;
```

To access a variable from that structure you can do this:

```
#include <cs50.h>
#include <stdio.h>

typedef struct
{
	string name;
	int age;
}
person;

int main(void)
{
	person man;
	man.name = "Joe";
	man.age = 54;
}
```
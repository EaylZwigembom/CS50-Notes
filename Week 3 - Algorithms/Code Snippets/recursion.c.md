#C #code-snippet 

```
#include <cs50.h>
#include <stdio.h>

void draw(int n);
  
int main(void)
{
    int height = get_int("Height: ");
    draw(height);
}  
  

void draw(int n)
{
    if (n <= 0)
    {
        return;
    }
  
    draw(n - 1);  

    for (int i = 0; i < n; i++)
    {
        printf("#");
    }
    printf("\n");
}
```

If you don't understand how this works:

When calling the function draw(n-1) it first waits for that call to finish before it goes on to the for loop. So it actually starts with printing the top layer which is just a single brick. 

Workflow of that function:

draw function (n = 4)
ok, let's first call draw(n -1) and only after that call is finished I can move on to the for loop

draw function (n = 3)
ok, let's first call draw(n -1) and only after that call is finished I can move on to the for loop

draw function (n = 2)
ok, let's first call draw(n -1) and only after that call is finished I can move on to the for loop

draw function (n = 1)
ok, let's first call draw(n -1) and only after that call is finished I can move on to the for loop

draw function (n = 0)
Ok, if n is or smaller than or equal to 0 then I don't do nothing. So I pretty much finished here

draw function (n = 1)
ok, that function I called just returned so I can move on to the for loop:
**prints a single hash because n = 1**
**function finishes**

draw function (n = 2)
ok, that function I called just returned so I can move on to the for loop:
**prints a 2 hashes because n = 2**
**function finishes**

draw function (n = 3)
ok, that function I called just returned so I can move on to the for loop:
**prints a 3 hashes because n = 3**
**function finishes**

draw function (n = 4)
ok, that function I called just returned so I can move on to the for loop:
**prints a 4 hashes because n = 4**
**function finishes**

Final Output: 
![[Pasted image 20250721111407.png]]




[[Recursion]]
[[Algorithms]]

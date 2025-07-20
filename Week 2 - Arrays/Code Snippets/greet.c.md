#C #code-snippet 

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

[[Command Line Arguments]]
[[Arrays]]


#C #code-snippet 

```
#include <cs50.h>
#include <stdio.h>
#include <string.h>

long Length(string stri);

int main(void)
{
    string name = get_string("What's your name ");
    int length = strlen(name);
    printf("%li\n", length);
}
```

[[Strings]]

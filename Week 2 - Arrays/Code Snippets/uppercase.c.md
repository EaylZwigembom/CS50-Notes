#C #code-snippet 

```
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string s = get_string("Before: ");
    printf("After: ");
    for (int i = 0, length = strlen(s); i < length; i++)
    {
        if (s[i] >= 'a' && s[i] <= 'z')
        {
            printf("%c", toupper(s[i]));
        }
    }
    printf("\n");
}
```

[[Arrays]]
[[Strings]]
[[ASCII]]
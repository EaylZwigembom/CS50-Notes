#C #code-snippet

```
#include <stdio.h>
#include <cs50.h>

float Average(int length, int scores[]);

const int N = 3;

int main(void)
{
    int scores[N];
    for (int i= 0; i < N; i++)
    {
        scores[i] = get_int("Score number %i: ", i + 1);
    }
    printf("Your average is: %f\n", Average(N, scores));
}

float Average(int length, int scores[])
{
    int sum = 0;
    for (int i = 0; i < length; i++)
    {
        sum += scores[i];
    }
    return sum / (float) length;
}
```

[[Arrays]]
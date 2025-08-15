#python

In C, you might remember this code:
```
    // get_string and printf with %s
    
    #include <cs50.h>
    #include <stdio.h>
    
    int main(void)
    {
        string answer = get_string("What's your name? ");
        printf("hello, %s\n", answer);
    }
```

This code is transformed in Python to:
```
    # get_string and print, with concatenation
    
    from cs50 import get_string
    
    answer = get_string("What's your name? ")
    print("hello, " + answer)
```

You can write this code by executing `code hello.py` in the terminal window. Then, you can execute this code by running `python hello.py`. Notice how the `+` sign concatenates `"hello, "` and `answer`.

Similarly, this can be done without concatenation:
```
    # get_string and print, without concatenation
    
    from cs50 import get_string
    
    answer = get_string("What's your name? ")
    print("hello,", answer)
```

Notice that the print statement automatically creates a space between the `hello` statement and the `answer`.

Similarly, you could implement the above code as:
```
    # get_string and print, with format strings
    
    from cs50 import get_string
    
    answer  = get_string("What's your name? ")
    print(f"hello, {answer}")
```

Notice how the curly braces allow for the `print` function to interpolate the `answer` such that `answer` appears within. The `f` is required to include the `answer` properly formatting.
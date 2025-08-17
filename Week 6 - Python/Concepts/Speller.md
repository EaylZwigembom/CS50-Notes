#python

To illustrate this simplicity, let’s type ‘code dictionary.py’ in the terminal window and write code as follows:

```
    # Words in dictionary
    words = set()
    
    
    def check(word):
        """Return true if word is in dictionary else false"""
        return word.lower() in words
    
    
    def load(dictionary):
        """Load dictionary into memory, returning true if successful else false"""
        with open(dictionary) as file:
            words.update(file.read().splitlines())
        return True
    
    
    def size():
        """Returns number of words in dictionary if loaded else 0 if not yet loaded"""
        return len(words)
    
    
    def unload():
        """Unloads dictionary from memory, returning true if successful else false"""
        return True
```

Notice that there are four functions above. In the `check` function, if a `word` is in `words`, it returns `True`. It is so much easier than an implementation in C! Similarly, in the `load` function, the dictionary file is opened. For each line in that file, we add that line to `words`. Using `rstrip`, the trailing new line is removed from the added word. `size` simply returns the `len` or length of `words`. `unload` only needs to return `True` because Python handles memory management on its own.

The above code illustrates why higher-level languages exist: To simplify and allow you to write code more easily.

However, speed is a tradeoff. Because C allows you, the programmer, to make decisions about memory management, it may run faster than Python – depending on your code. While C only runs your lines of code, Python runs all the code that comes under the hood with it when you call Python’s built-in functions.

You can learn more about functions in the [Python documentation](https://docs.python.org/3/library/functions.html)


[[Filter]]
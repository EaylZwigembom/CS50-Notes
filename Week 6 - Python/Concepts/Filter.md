#python

To further illustrate this simplicity, create a new file by typing `code blur.py` in your terminal window and write code as follows:

```
    # Blurs an image
    
    from PIL import Image, ImageFilter
    
    # Blur image
    before = Image.open("bridge.bmp")
    after = before.filter(ImageFilter.BoxBlur(1))
    after.save("out.bmp")
```

Notice that this program imports modules `Image` and `ImageFilter` from a library called `PIL`. This takes an input file and creates an output file.

Further, you can create a new file called `edges.py` as follows:
```
    # Finds edges in an image
    
    from PIL import Image, ImageFilter
    
    # Find edges
    before = Image.open("bridge.bmp")
    after = before.filter(ImageFilter.FIND_EDGES)
    after.save("out.bmp")
```

Notice that this code is a small adjustment to your `blur` code but produces a dramatically different result.

 Python allows you to abstract away programming that would be much more complicated within C and other __lower-level__ programming languages.
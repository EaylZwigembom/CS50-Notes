#code-snippet #python 

```
from PLI import image, ImageFilter

before = Image.open("bridge.bmp")
after = before.filter(ImageFilter.BoxBlur(10))
after.save("out.bmp")
```

**Note:** The number in BoxBlur() is the number of pixels were looking at and making boxes from
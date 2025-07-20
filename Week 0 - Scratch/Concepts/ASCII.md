#ACII

![](https://lh7-rt.googleusercontent.com/slidesz/AGV_vUcUQrgWn-s_8iZsgmLHP_1i3Ke8c3UoGo5xSuuyYt_CXiFCknNa4TpL4xnkvJtNF5HaDj-EvdJRL0T_14VWVOCXiv5ihgGyzvtIom6AFIv6fqTJ0RfpkGyV6gEWoyzJXD5di2U26usNLZHXDu8L6NKLbaS9-2oF=s2048?key=13zS9y-MjjTHuAQkELahQA)

**ASCII** (American Standard Code for Information Interchange) is a system to 
**==assign numbers** to **characters**== such as **letters** from the alphabet, and other symbols,
so we can turn **bytes**([[Binary#^bytes]]) into other things than numbers (Letters, symbols, etc...). Each **byte** is enough to represent each symbol or character from the ASCII table. But 256 options is not enough for all of the languages, so computers don't use just **7** or **8** bits. For some languages they use **16**, **32** or even **64** bits. 

For Example
The letter A (In capital) was decided to be represented by the number 65 (01000001).

 **Fun fact:** **32** bits can represent as many as **4 billion** possible characters. and **4 billion** characters is a lot more than enough for all of the languages in the world. so people have started **representing** things that are not just letters, numbers, or symbols. **For further explanation go to -->** [[Unicode]]

##### Chars
^chars

if you want to change a char from lowercase to uppercase or the other way around. **==Because chars are just numbers you can change them mathematically==**. In the ASCII chart the **distance** between a character that is **uppercase** from the same character that is **lowercase** is **32**. so If you want to change the character from **lowercase to uppercase** you **subtract** from the char 32 and if you want to change a character from uppercase to lowercase you **add** 32

```
#include <cs50.h>
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
            int upperCase = s[i] - 32;
            printf("%c", upperCase);
        }
        else
        {
            printf("%c", s[i]);
        }
    }
    printf("\n");
}
```

Here is an example of a program that prompts the user for a string and it turns the whole string into uppercase.
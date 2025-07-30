hexadecimal is a method for representing numbers in a computer:

You represent the colors this way:

#000000

There is an hash sign and then 6 digits. Every 2 digits represents a color

The hexadecimal way of counting goes like this:

0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F

Because computer scientist didn't want to represent 2 digit numbers with 2 digits the just added letters to it: A represents 10, B, represents 11, and so through until F that represents 15.

the hexadecimal is counted in base-16:

![[Pasted image 20250729111419.png]]

Well, let's make it more simple: 16^0 = 1, 16^1 = 16:

![[Pasted image 20250729111457.png]]

00 represents 0: (0 * 1) + (0 * 16) = 0
01 represents 1: (1 * 1) + (0 * 16) = 1
10 represents 16: (0 * 1) + (1 * 16) = 16
0F represents 15: (15 * 1) + (0 * 16) = 15
FF represents 255: (15 * 16) + (1 * 15) = 255

FF is the highest number in hexadecimal and it represents 255.

In the computer's system to differentiate between regular numbers and hexadecimal numbers before every hexadecimal number there is an 0x and it means that this number is an hexadecimal number. But why to differentiate?

Because when reading a number 10. it can mean both 10 (in decimal) and it can also mean 16 (in hexadecimal). so we basically just put 0x to mark that the number is hexadecimal.

Computer use hexadecimal numbers for pointers in memory because the hex system requires less bits than decimal numbers and it's easier to read than just binary numbers.
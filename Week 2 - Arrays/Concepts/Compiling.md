#C #Compiling


![[Pasted image 20250619160349.png]]
**Compiling** is the **==process of taking your input which is the ==**
**==source code(C, Java, Swift, etc...) and turning it into what's called 
machine code==** ([[Binary]]). The **compiler** is an **algorithm**([[Algorithms]]), embodied in a **program** that we can run. But how do we actually get from source code to machine code?

Well, up until now, when you want to **compile** a program
(Let's say the name of the program will be: **hello**).

You write:
```
make hello
./hello
```

which is a bit weird, but **make** **hello** says: **==compile the program called hello==**
and **./hello** says: **==run the program called hello in the current folder==**. This command is equivalent to double clicking an icon of an app in your desktop.

But the command "**make**" is **not** actually a compiler. It is a **program**, a very helpful program, but it **==automates the process of running an actual compiler for you==**.

```
clang hello.c
./a.out
```
There's **many** different compilers in the world but the one we will use in this class is free, and open-source, and therefor very popular in the world, is actually called: **==clang (For: C Language)==**. And so really what's happening when you run **make hello** or any other such command in turn is running another program for you called **==clang==**. 
The catch though is that this program by default **==is not nearly as user friendly==**. and it doesn't even give you a useful input. By default the program that the clang gives you is called **a.out**. which is stands for **Assembly Output**. So how can we make the name of the program make more sense? 

Well we can use what's called 
[[Command Line Arguments]]. In **clang** we can do this by instead of just typing clang, and the name of the source code, we can add an **==argument==** before the name of the program to change the name:

```
clang -o hello hello.c
./hello
```
So you see that there is this **==-o==** in the program and this thing is called a 
**flag or a switch**(Whichever you would like to call it), which is basically an **argument** that helps you modify the command. This command says: **==Output(From here comes -o) a file named hello when you compile hello.c. ==**

```
clang -o hello hello.c -lcs50
./hello
```
But, when you use a **==third-party library==**(**A library that someone else made**), let's say for this instance: the cs50 library, You have to **state** that you are using that library by typing **-l** in the way seen above.
You have to do that because **third-party libraries** are not a part of the actual programming language so the compiler won't know about the library unless you've **pre-installed** it.


But what does **compiling** even mean? We said before compiling is **==turning source-code into machine code==**, but that's actually an abstraction, it was a simplification of a **multi-step process** that the computer's actually doing for you. So it turns out, that when you run **make**, and in turn it runs clang. **4 separate things are happening**, each of which does something a little different for you:

**Preprocessing**
**compiling**
**assembling**
**linking**

Now let's take a deeper dive into each step of the process:

##### **Preprocessing**

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	string name = get_string("Whatt's your name? ");
	printf("Hello, %s\n", name);
}
```

Here is one of the programs that was written in week 1(No notes).
This program prompted the user for it's name and then
said hello, + the user's name.

Now, what the **preprocess** is actually doing is **==taking the code you are using from the library and is copy-pasting a prototype of the function you are using on the top of the program==**. So the code will look something like this:

```
string get_string(string promt, string value);
int printf(string foramt, ...);

int main(void)
{
	string name = get_string("Whatt's your name? ");
	printf("Hello, %s\n", name);
}
```

Everything that starts with **#** is called a **preprocessor directive**. It means that **==there's something in that file that you want it to get copy-pasted into your code==**. So again, what's the preprocessor does is going through the code in the **library** and copy-pasting the code in your program (For this example is pasting all of the code from the stdio and cs50 libraries). 
##### **Compiling**
Here is what happens when you actually **compile** the code.

```
string get_string(string promt, string value);
int printf(string foramt, ...);

int main(void)
{
	string name = get_string("Whatt's your name? ");
	printf("Hello, %s\n", name);
}
```

Here is the **preprocessed** code that we covered earlier. And when you actually compile this code, it means **==it gets translated from one language, C in this case, to another language called assembly code==**:

```
...
main: 
    .cfi_startproc
# BB#0:
    pushq    %rbp
.Ltmp0:
    .cfi_def_cfa_offset 16
.Ltmp1:
    .cfi_offset %rbp, -16
    movq    %rsp, %rbp
.Ltmp2:
    .cfi_def_cfa_register %rbp
    subq    $16, %rsp
    xorl    %eax, %eax
    movl    %eax, %edi
    movabsq    $.L.str, %rsi
    movb    $0, %al
    callq    get_string
    movabsq    $.L.str.1, %rdi
    movq    %rax, -8(%rbp)
    movq    -8(%rbp), %rsi
    movb    $0, %al
    callq    printf
    ...
```

**Assembly** is the language of the CPU your computer. CPUs don't understand C, they don't understand Scratch. They do understand **0's** and **1's** but they even more understand **assembly code**. **==Assembly code is basically commands that were programmed into the CPUs==** and each command represents a unique pattern of 0's and 1's. When you buy a CPU you can see a guide to it's **assembly code** in the manual. Each CPU type has it's own unique commands in assembly code.
##### **Assembling**
Assembling is **==the process is converting the assembly code into 0's and 1's==**

```
...
main: 
    .cfi_startproc
# BB#0:
    pushq    %rbp
.Ltmp0:
    .cfi_def_cfa_offset 16
.Ltmp1:
    .cfi_offset %rbp, -16
    movq    %rsp, %rbp
.Ltmp2:
    .cfi_def_cfa_register %rbp
    subq    $16, %rsp
    xorl    %eax, %eax
    movl    %eax, %edi
    movabsq    $.L.str, %rsi
    movb    $0, %al
    callq    get_string
    movabsq    $.L.str.1, %rdi
    movq    %rax, -8(%rbp)
    movq    -8(%rbp), %rsi
    movb    $0, %al
    callq    printf
    ...
```

Here is the assembly code that we covered earlier and here is how it should look like in 0's and 1's:

```
01111111010001010100110001000110
00000010000000010000000100000000
00000000000000000000000000000000
00000000000000000000000000000000
00000001000000000011111000000000
00000001000000000000000000000000
00000000000000000000000000000000
00000000000000000000000000000000
00000000000000000000000000000000
00000000000000000000000000000000
10100000000000100000000000000000
00000000000000000000000000000000
00000000000000000000000000000000
01000000000000000000000000000000
00000000000000000100000000000000
00001010000000000000000100000000
01010101010010001000100111100101
01001000100000111110110000010000
00110001110000001000100111000111
01001000101111100000000000000000
00000000000000000000000000000000
00000000000000001011000000000000
11101000000000000000000000000000
00000000010010001011111100000000
00000000000000000000000000000000
00000000000000000000000001001000
...
```

No human should understand this version of code just by reading it. They can maybe get some paper and pencil and try to decode it, but it will be very hard.
##### **Linking**
Linking is pretty simple. When you use libraries it's basically another code in addition to your own code. Let's use the same code for example:

```
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	string name = get_string("Whatt's your name? ");
	printf("Hello, %s\n", name);
}
```

In this program there are actually 3 files: the cs50 library, the stdio library, and finally, your own program. So that means there will be 3 sets of 0's and 1's. So what's the linking process is doing is ==**just mashing them up together into one set of 0's and 1's.**==
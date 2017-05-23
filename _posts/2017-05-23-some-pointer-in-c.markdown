---
layout: post
title:  "Pointer in C"
date:   2017-05-23 22:53:04 +0700
categories: C
---
I'm learning C, and below are some interesting points that I want to take notes:

- If we create a variable like:

{% highlight c %}
int a = 5;
{% endhighlight %}

It will store that variable in the `Stack`. Where as if we use:

{% highlight c %}
char *b = malloc(sizeof(char)):
*b = 'z';
{% endhighlight %}

then that variable will be stored permanently (if we don't free it) in the `Heap`. That's why if we print the address of variable a each time the program run, it will change unlike variable b.

- If we create a pointer like this

{% highlight c %}
char *d = malloc(sizeof(char)*10);
{% endhighlight %}

then how can we assign it like this?

{% highlight c %}
d = "foo bar";
{% endhighlight %}

`d` is a pointer right? Actually the string on the right return the address so the variable d can be assigned that address

- Printing string

{% highlight c %}
char *d = malloc(sizeof(char)*10);
d = "foo bar";
printf("%p\n", d+2);
printf("%s\n", d+2);
printf("%c\n", *(d+2));
{% endhighlight %}

If `d` is a pointer, can you guess what would be printed in each line?
Answer: 1.some hex number showing the address of the pointer; 2. the string "o bar"; 3. the character "o"

- I've seen 2 ways of writing the arguments argv:

{% highlight c %}
// first way
int main(int argc, char *argv[])
{}

// second way
int main(int argc, char **argv)
{}
{% endhighlight %}

Both is correct, because - minor some minor details - they are kind of the same.
Declaring char *a and char a[] are the same thing, `a` will be the pointer in both cases. When we call `a`, it will return the value from that pointer onward until it meets the `\0` character.

- Why 32-bit OS can handle only 4GB of RAM? Maybe because the memory address can have only 4 bytes? So the largest address will have the value of 0xffffffff. Divide this by 1024*3 will yield the result of 4.

- Above, we experiment with pointer arithmetic, but if we have the code like this:

{% highlight c %}
int x = 42;
int *y = &x;

// if y is 0x00, y+1 would be 0x04, not 0x01
// because it takes account of the size of int (4 bytes) for each
// incremental
{% endhighlight %}

- And that also tells us something about array syntax, they're just syntactic sugar

{% highlight c %}
// *a is a[0]
// *(a+1) is a[1]
// *(a+2) is a[2]
{% endhighlight %}

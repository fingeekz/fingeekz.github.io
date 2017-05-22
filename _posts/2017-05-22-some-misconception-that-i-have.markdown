---
layout: post
title:  "Some misconception that I've had for... 1 year of coding"
date:   2017-05-22 22:25:04 +0700
categories: general
---
Okay boys we will go straight to the point, starting with the least interesting thing:

- `md... what the hell is md?`: If you are not living under a rock, in a cave or on the cloud, you would find every serious git repository either on Bitbucket or Github has a file named... you guess it... README.md
Since the begining of my coding career, I've always wondered what that md means. Asking my peers and superiors and they either don't know or don't care or both. Until this day when I'm blogging this post, finally it hits me (well maybe because this file here has the extension of .markdown), it's MarkDown! Okay...
TL;DR: Mark Down

- `SSH in Github or Bitbucket`: Initially, I thought the SSH's purpose is for encrypting the data transmitting between the client and the git server. After sometime when I learnt about the Asymmetric Encryption, another question popped up in my head: "if only the client has the private key, then only the client can decrypt the message that the server sends, then how the data gets encrypted?".
Turns out, the git server only uses the SSH to authenticate the client, by usingg the client's public key to encrypt a message, send that to the client, if the client can decrypt that message then it gets authorized.
How can the git server know which public key to use to encrypt the message for a client? You can see more detail here: {{ "https://stackoverflow.com/questions/23580283/how-does-ssh-public-key-authentication-work-picking-up-right-keys" | uri_escape }}

- `pointer, address variable in C`: Truth be told, my major in university is Business Administration, not Computer Science... That's why I'm learning CS50 on EDX (fantastic course, everyone should try it!). I'm at the part of learning about the pointer and address of a variable, about memory allocation in C.
Before, I always thought that in the statement
{% highlight c linenos%}
int *a;
{% endhighlight %}

"int" would mean the type of the memory block to be int, and "*a" would be the variable name of a pointer. So "a" would always be a variable with the real data, right?
I couldn't be more wrong. "int *" is really a type of its own, its like "int" or "char" or any other types.
"int *" is the type of a pointer that will store "int", "char *" would be a type of a pointer store "char". Try to experiment it and you will see, the error when compile will tell us the truth!
so then "int *a" would be assign a pointer to a variable named "a", with type "int *".

So if we have something like:
{% highlight c linenos%}
int main()
{
    int *d = malloc(7);
    char z = 'a';
    d = &z;
    printf("%p\n", d);
    printf("%d\n", *d);
    return 0;
}
{% endhighlight %}

"d" would be a pointer address, print "d" will just print the address,
print "*d" will print the actual value, since "*d" will extract the data from the address "d" to the \0 block,
and then lastly "&z" is kind of reverse from "*d", it extracts the address from a variable that stores real data.



Well, that's it for today. I'm just blogging this to cement my knowledge, so if there's any misinformation (and I suspect there would be) please don't hestitate to correct me,
The least thing I want to do is spreading misinformation :)

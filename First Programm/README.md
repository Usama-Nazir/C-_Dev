1.1.1 Writing your first program

Now we’re going to show you a very simple (and, at the same time, completely useless) program written in the C++ language. We’re going to use this example to present you some basic rules governing the language. The program itself will be modified many times, as it becomes enriched by various additional elements in expanding our programming knowledge. Ready? All right then, let’s go.

First we need to define our expectations for the program. They’ll be very modest. We want a short text to appear on the screen. Let's assume that the text will state:


It's me, your first program.
Output

That’s all we want at the moment.

What further steps should our first program perform? Let's try to enumerate them here:

to start;
to write the text on the screen;
to stop
This type of structured and semi-formal description of each step of the program is called an algorithm. Sources of the word algorithm can be traced back to the Arabic language and originated in early medieval times, and for us, this represents the beginning of computer programming.

Okay, it's time to see our program. Have a look at the code in the editor:


play_arrow
sync
download
light_mode
dark_mode
Console 
terminal
sync

It looks a bit mysterious, doesn't it? Let’s check out each line of the program carefully, and uncover its meaning and purpose. The description is not particularly accurate and those of you who know a little C++ already will probably conclude that it’s too simplistic and somewhat childish. We did this on purpose – we’re not building Rome in a day. Not even in a week!

Let's move on.

Pay attention to the character # (hash) at the beginning of the first line. It means that the content of this line is the so-called preprocessor directive. We’re going to tell you more about the preprocessor later, but for now we’ll only say that it’s a separate part of the compiler whose task is to pre-read the text of the program and make some modifications in it. The prefix "pre" suggests that these operations are performed before the full processing (compilation) takes place.

The changes the preprocessor will introduce are fully controlled by its directives. In our program, we are dealing with the include directive. When the preprocessor meets that directive, it replaces the directive with the content of the file whose name is listed in the directive (in our case, this is the file named iostream). The changes made by the preprocessor never modify the content of your source file in any way. Any alterations are made on a volatile copy of your program that disappears immediately after the compiler finishes its work.

So why do need the preprocessor to include the content of a completely unknown file called iostream? Writing a program is similar to building a construction with ready-made blocks. In our program, we are going to use one such block and it will happen when we want to write something on the screen. That block is called cout (you can find it inside our code), but the compiler knows nothing about it so far. In particular, the compiler has no idea that cout is a valid name for that block while cuot isn't. The compiler must be warned about it – it needs to be aware of the fact.

A set of preliminary information that the compiler needs is included in header files. These files contain a collection of preliminary information about ready-made blocks which can be used by a program to write text on the screen, or to read letters from the keyboard. So when our program is going to write something, it will use a block called cout, which is able to do the trick (and much more). We don't want the compiler to be surprised, so we need to warn it about that. The compiler’s developers put a set of this anticipatory information in the iostream file. All we have to do is use the file. This is exactly what we expect from the include directive.

But where is the iostream file located? The answer is simple, but not as clear as you might want: that’s not our problem. The preprocessor knows where it is. Good job, preprocessor!

In the C++ language, all elements of the standard C++ library are declared inside the namespace called std. A namespace is an abstract container or environment created to hold a logical grouping of unique entities (blocks).

An entity defined in a namespace is associated only with that namespace. If you want to use many of the standard C++ entities (we’re going to tell you all about them later) you must insert the using namespace instruction at the top of each file, outside of any function.

The instruction should specify the name of the desired namespace (std in our case). This will make the standard facilities available throughout the program.

We’ve already said something about the blocks. Now let's go a little deeper. One of the most common types of blocks used to build C++ programs are functions.

If you associate a function with mathematics, you’re on the right track. Imagine a function as a black box, where you can insert something into it (though this is not always necessary) and take something new out of it, as if from a magic hat. Things to be put into the box are called function arguments (or function parameters). Things to be taken out of the box are called function results. In addition, a function can do something else on the side.

If this sounds rather vague, don't worry, we’ll talk about functions many times and in much more detail later.

Back to our program. The standard of the C++ language assumes that among many different blocks that may be put into a program, one specific block must always be present, otherwise the program won't be correct. This block is always a function with the same name: main.

Every function in C++ begins with the following set of information:

what is the result of the function?
what is the name of the function?
how many parameters does the function have and what are their names?
Take a close look at our program and try to read it properly, accepting the fact that you won’t yet fully understand everything.

wthe result of the function is an integer value (we can read it from the word int, which is short for integer)
the name of the function is main (we know why already)
the function doesn't require any parameters (which we can read from the word void).
This set of information is sometimes called a prototype, and it’s like a label affixed to a function announcing how you can use that function in your program. The prototype says nothing about what the function is intended to do. It’s written inside the function and the interior of the function is called the function body. The function body begins with the first opening bracket { and ends with the corresponding closing bracket }. It might sound surprising, but the function body can be empty, which means that the function does exactly nothing.

We can even create a function that is lazy – it can be encoded like this:



void lazy(void) { }

This drone provides no result (the first void), its name is "lazy", it doesn't take any parameters (the second void) and it does absolutely nothing (the blank space between brackets).

By the way, the names of the functions are subject to some fairly rigid constraints. More on this later.

Inside the main function body we need to write what our function (and thus the program) is supposed to do. If we look inside, we find a reference to a block named cout.

Firstly, note the semicolon at the end of the line. Each instruction (more precisely, each statement) in C++ must end with a semicolon – without it the program will be incorrect.

This particular statement says: instruct the entity named cout to show the following text on the screen (as indicated by the << digraph, which specifies the direction in which the text is sent). You might ask – how do we know that cout will do that for us? Well, we know it because it says so in the C++ language standards.

The cout entity (in fact, it's an object, but we don't want to bring up this word too soon – more on it later) must be fed with something that is intended to be shown on the screen. In our example, the feed is just text (string). For simplicity, we can assume that strings in the program in C++ are always enclosed in quotes – that way the compiler recognizes the text that is sent to the user of the program, and the text that is intended to be compiled is translated into machine language. This distinction is very important. Take a look:




The line above is the main function prototype.




"int main(void);"

The line above is not the main function prototype, but a string that only looks like part of a source code. The compiler is not interested in what is between the quotes, and therefore doesn’t recognize such strings as code.

How does it work? We can picture it like this: the execution of our main function is suspended (we can say that the main function falls asleep) and during that time cout, together with << (this kind of symbol is named operator) prints the text on the screen. When the text is printed, the main function wakes up and continues its activity.

The above form of source code is the most natural and perhaps the most easily read by humans, but you’re still free to write it in a different way. For example:



cout
<<
"It's me, your first program."
;

In the C++ language it isn’t necessary to write just one statement per line. You can place two (or more) statements on the same line, or split one statement into several lines, but bear in mind that readability (for humans) is a very important factor. However, compilers, unlike humans, will never complain about your style.

We’re almost at the end now. There’s only one line left in our program. This is:



return 0;

This is another (beside the function invocation) statement of the C++ language. Its name is just return and that’s what it does. Used in the function, it causes the end of function execution. If you perform return somewhere inside a function, this function immediately interrupts its execution.

The zero after the word return is a result of your function main. It's important - this is how your program tells the operating system the following: I did what I had to do, nothing prevented me from doing this, and everything is okay.

If you were to write:



return 1;

this would mean that something had gone wrong, it did not allow your program to be performed successfully and the operating system could use that information to react appropriately.

So is that all? Yes, that’s it! Let's look again at our program and see what’s happening step by step:

we introduced the function named main into our program - it will be executed when you start the program;
we made use of an entity named cout inside the main function - it will print the text on the screen;
the program finishes immediately after printing, indicating that everything you expected to achieve has been achieved.
So hopefully it wasn’t as difficult as it seemed at first glance. Now let’s try to persuade the computer to compute something for us – after all, that’s what they’re for.
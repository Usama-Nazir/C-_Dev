1.3.1 Floating-point numbers
A word (or 2.0 words) about floating-point numbers in real life and in the C++ language.

Previously, we became acquainted with the concept of data type, and learned that one of the basic types known in the C++ language is the integer type named int. Now it's the time to talk about another type, designed to represent and store the numbers that (as a mathematician would say) have a non-empty decimal fraction.

These are the numbers that have (or may have) a fractional part after the decimal point, and although this is a very simplistic definition, it is sufficient for our purposes. Whenever we use a term like "two and a half" or "zero point four" we think of numbers which the computer considers to be floating numbers.




Let's go back to the values we quoted a moment ago. "Two and a half" looks normal when you write it in a program, although if your native language uses a comma instead of a point in the number, you should make sure that your number contains points and not commas. The compiler will either not accept it or (in very rare circumstances) will misunderstand your intentions, as the comma itself has its own reserved meaning in the C++ language.

If you want to use a value of just "two and a half", you should write it as shown here:



2.5

Note once again – there is a point between "2" and "5" - not a comma.

As you can probably imagine, you can write the value of "zero point four" in C++ as:



.4

Don’t forget this simple rule – you can omit zero when it’s the only digit in front of or after the decimal point. In essence you can write the value 0.4 like on the right.

For example: the value of 4.0 could be written as 4. without changing its type or value.

Note: the decimal point is essential to recognize floating-point numbers in C++. Look at these two numbers:



4
4.0

You might think that they’re exactly the same, but the C++ compiler sees them completely differently:


4 is an int.


4.0 is a float.


We can say that the point makes a float.

Don't forget that.



When you want to use any numbers that are very large or very small, you can use so-called scientific notation. Take, for example, the speed of light expressed in meters per second. Written directly it would look like:


300000000



To avoid the tedious job of writing of so many zeros, physics textbooks use an abbreviated form, which you’ve probably seen already:

3 • 108

It reads: "three times ten to the power of eight"

In the C++ language, the same effect is achieved in a slightly different form – take a look:



3E8

The letter E (you can also use the lower case letter e – it comes from the word exponent) is a concise version of the phrase "times ten to the power of".

Note:

the exponent (the value after the "E") has to be an integer.
the base (the value in front of the "E") may or may not be an integer.
Let's see how we use this convention to record numbers that are very small (in the sense of their absolute value, which is close to zero). A physical constant called Planck's constant (and denoted as h) has, according to the textbooks, the value of:

6.62607 x 10-34

If you would like to use it in a program, you would write it this way:



6.62607E-34

And that’s it. Not so hard, right?





Let's go back to the floating-point values. We already know what a variable is, and we also know how to declare an integer variable, so now it’s time to declare variables of a floating-point type.

We do this using the keyword float. Knowing that we can declare two floating-point variables, named PI (we can't name it Π because - as you already know - the C++ language freaks out when variable names are written with Greek letters) and Field:



float PI, Field;

As you can see, the difference in declaring the integer and float variables is quite small from the syntax's point of view.


This difference in terms of semantics is significant, as you can see in the example below. With a little thought, we can figure out that the symbol (more precisely - the operator) that performs the mathematical division is a single character / (slash). Take a look at the code:



int i;
float x;

i = 10 / 4;
x = 10.0 / 4.0;

It might be a bit surprising for you to know that the value that will be entered in the variable i is 2 (yes - just 2!) while the variable x will be equal to 2.5. Look at the example carefully, because it illustrates a very important difference between these two data types.


What happens when we have to convert integer values into float values or vice versa? We can always transform from int into float, but it can lead to a loss of accuracy. Consider the example below:



int i;
float f;

i = 100;
f = i;

After changing from int to float, the value of the variable f is 100.0, because the value of type int (100) is automatically converted into a float (100.0).

The transformation affects the internal (machine) representation of those values as computers use different methods for storing floats and ints in their memory.


Let's consider the opposite situation now.

As you’ve probably guessed, these substitutions will result in a loss of accuracy - the value of the variable i will be 100. Twenty-five hundredths has no meaning in the ints world. Furthermore, converting a float into an int is not always feasible.



int i;
float f;

f = 100.25;
i = f;

Integer variables (like floats) have a limited capacity. They cannot contain arbitrarily large (or arbitrarily small) numbers.

For example, if a certain type of computer uses four bytes (i.e. 32 bits) to store int values, you can only use the numbers from the range of -2147483648 to 2147483647.


The i variable is unable to store such a large value, but it isn’t clear what will happen during the assignment. Certainly a loss of accuracy will occur, but the value assigned to the variable i is not known in advance.

In some systems it may be the maximum permissible int value, while in others an error occurs, and in others still the value assigned can be completely random.

This is what we call an implementation dependent issue. It's the second (and uglier) face of software portability.



int i;
float f;

f = 1E10;
i = f;

1.3.2 Operators
An operator is a symbol of the programming language, which is able to operate on the values. For example, an assignment operator is the = sign. We already know that it can assign values to variables.


Now let’s look at some other operators available in the C++ language and find out which rules govern their use and how to interpret the operations they perform.

Let’s begin with the operators associated with widely recognizable arithmetic operations.

The order of their appearance is not accidental.

We’ll talk more about this afterward.



1.3.3 Multiplication
An asterisk * is a multiplication operator. If you take a look at the code here, you’ll see that the variable k will be set to the value of 120, while the z variable will be set to 0.625.



int i, j, k;
float x, y, z;

i = 10; 
j = 12;
k = i * j;
x = 1.25; 
y = 0.5;
z = x * y;

1.3.4 Division
A slash ("/") is a divisional operator. The value in front of the slash is a dividend, the value behind the slash, a divisor. Look at the snippet of the program below: of course, k will be set to 2, z to 0.5.



int i, j, k;
float x, y, z;

i = 10; j = 5;
k = i / j;
x = 1.0; y = 2.0;
z = x / y;

1.3.5 Division by zero
As you’ve probably guessed, dividing by zero is strictly forbidden, but the penalty for violating that rule will come to you at different times.



float x;

x = 1.0 / 0.0;

If you dare to write something like that, the compiler will go nuts – you’ll get a compilation error, runtime error or some message at runtime, possibly also a few choice words about your programming capabilities. OK, the last one was a joke. Still, in some cases you won't be able to run your program. As a general rule, you shouldn't divide by zero.


In the following example the compiler won't tell you a thing, but when you try to execute that code, the result of the operation may be surprising. It’s not a number. It’s a special featured value named inf (as in infinitive). Generally, this kind of illegal operation is a so-called exception.



float x, y;

x = 0.0;
y = 1.0 / x;

When you find exceptions in your program, you should react accordingly. We’ll discuss this later.

1.3.6 Addition
The addition operator is the "+" (plus) sign, which most of us already know from maths class. Again, take a look at the snippet of the program – as you can surmise, k is equal to 102 and z to 1.02.



int i, j, k;
float x, y, z;

i = 100; j = 2;
k = i + j;
x = 1.0; y = 0.02;
z = x + y;

1.3.7 Subtraction
The subtraction operator is obviously the "-" (minus) sign, although you should note that this operator also has another meaning – it can change the sign of a number. This is a good time to show you a very important distinction between unary and binary operators (in the C++ language there is also a ternary operator – more on that a bit later).

As usual, let’s get acquainted with a snippet of the program – you can guess that k will be equal to -100, while z will be equal to 0.0.



int i, j, k;
float x, y, z;

i = 100; j = 200;
k = i - j;
x = 1.0; y = 1.0;
z = x - y;

1.3.8 Unary minus
In "subtracting" applications, the minus operator expects two arguments: the left (a minuend in arithmetic terms) and the right (a subtrahend). For this reason, the subtraction operator is considered one of the binary operators, just like the addition, multiplication and division operators. But the minus operator may be used in a different way – take a look at the snippet.



int i, j;

i = -100;
j = -i;

As you’ve probably guessed, the variable j will be assigned the value of 100. We used the minus operator as a unary operator, as it expects only one argument – the right one.

1.3.9 Unary plus
The same dual nature is expressed by the "+" operator, which can be also used as a unary operator – its role is to preserve the sign. Take a look at the snippet.



int i, j;

i = 100;
j = +i;

Although such a construction is syntactically correct, using it doesn’t make much sense and it would be hard to find a good rationale for doing so.

1.3.10 Remainder
The remainder operator is quite peculiar, because it has no equivalent among traditional arithmetic operators.

Its graphical representation in the C++ language is the % (percent) character, which may look a bit confusing. It’s a binary operator (it performs the modulo operation) and both arguments cannot be floats (don't forget that!). Look at the example:



int i, j, k;

i = 13;
j = 5;
k = i % j;

The k variable is set to the value of 3 (because 2 * 5 + 3 = 13).

Oh, and one more thing you need to remember: you cannot compute the remainder with the right argument equal to zero. Can you guess why?

You probably remember what we said earlier about dividing by zero. And because division by 0 invokes undefined behaviour, the modulo operation, which relies on division, is undefined, too.

Well, that’s what the C++ Standard says. We have to accept that.

1.3.11 Priorities
So far, we’ve treated each operator as if it had no connection with the others. Of course, in real programming, nothing is ever as simple as that. Also, we very often find more than one operator in an expression and then things can get very complicated very quickly. Consider the following expression:



2 + 3 * 5

If your memory hasn't failed you, you should remember from school that multiplications precede additions. You probably remember that you have to multiply 3 by 5, keep the 15 in your memory, add it to 2, thus getting the result of 17.

The phenomenon that causes some operators to act before others is known as the hierarchy of priorities. The C++ language precisely defines the priorities of all operators and assumes that operators of larger (higher) priority perform their operations before the operators with lower priority.

So if we know that * has a higher priority than +, we can figure out how the final result will be computed.

1.3.12 Bindings
The binding of the operator determines the order of computations performed by some operators with equal priority, put side by side in one expression. Most operators in the C++ language have the left-sided binding, which means that the calculation of this sample expression is conducted from left to right, i.e. 3 will be added to 2, and 5 will be added to the result.



2 + 3 + 5

Now at this point you might be snorting and saying that all children know perfectly well that addition is commutative and it doesn’t matter in which order the additions are performed. And yes, you're right, but not quite. Additions performed by the computer are not always commutative. Really. We’ll show you this in more detail later. But for now, be patient and trust us.

1.3.13 Priority table
Since you're new to C++ language operators, presenting a complete list of operators' priorities may not be a good idea. Instead, we’ll show you its truncated form, and we’ll expand on it consistently during the introduction of new operators.

This table now looks as follows:

Note: we’ve gone through the operators in order from the highest to the lowest priority.



We want to check if you understand the concept of binding. Try to work through the following expression:


2 * 3 % 5

Both operators (* and %) have the same priority, so the result could be guessed only when you know the binding direction.

Do you know the result? Click Check below to see if you were right:


Check
1.3.14 Parentheses
Of course, we’re always allowed to use parentheses, which can change the natural order of calculation. Just like with arithmetic rules, subexpressions in parentheses are always calculated first. You can use as many parentheses as you need and we often use them to improve the readability of an expression, even if they don't change the order of operations.

An example expression involving multiple parentheses is given below. Try to compute the value given to the l variable.



int i, j, k, l;
i = 100;
j = 25;
k = 13;
l = (5 * ((j % k) + i) / (2 * k)) / 2;

Click Check below to see if you were right:


Check
1.3.15 Increment and decrement operators
Here are some operators in the C++ language which you won’t find in maths textbooks.

Some of them are frequently used to increment a variable by one. This is often done when we’re counting something (e.g. sheep). Let's consider the following snippet:



int sheep_counter;

sheep_counter = 0;



Every time a sheep runs through our thoughts we want the variable to be incremented, like this:



sheep_counter = sheep_counter + 1;

Similar operations appear very frequently in typical programs, so the creators of the C++ language introduced a set of special operators for these actions. One of them is the ++ (plus plus) operator. You can achieve the same effect in a shorter way:



sheep_counter++;

It looks much more elegant now, doesn't it?

Similarly, you can also decrease the value of a chosen variable. For example, if we can hardly wait for our holiday, our mind does the following operation every morning:



days_until_holiday = days_until_holiday - 1;

We can write it in a more compact way:



days_until_holiday--;



Sorry, but now we have to introduce a few new words.

The "++" is called the increment operator.

The "--" is called the decrement operator.

We’ve shown you the ++ and -- operators after a variable (a specialist in the syntax of programming languages would say that they’re used as postfix operators). However, both operators can be placed in front of a variable as well (as prefix operators), like this:



++sheep_counter;
--days_until_holiday;

The effect will be exactly the same: sheep_counter will be increased by 1, days_until_holiday decremented by 1. There’s a fairly significant difference, however, which is described by the precise names of these operators.

Here they are.

That may seem a little weird to you, but it’ll only take a short time to understand. Let's discuss the effects of these operators.


Operation:


++variable

--variable

Effect:

Increment/decrement the variable by 1 and return its value already increased/reduced.


Operation:


variable++

variable--

Return the original (unchanged) variable's value and then increment/decrement the variable by 1.


This behavior justifies the presence of the prefix pre- (before) and post- (after) in the operators’ names: pre- because the variable is modified first and then its value is used; post- because the variable's value is used and then modified.

1.3.16 Pre-and post-operators and their priorities
Take a look at two simple examples.



int i, j;

i = 1;
j = i++;

First, the variable i is set to 1. In the second statement, we’ll see the following steps:

the value of i will be taken (as we use the post-incrementation);
the variable i will be increased by 1.
In effect, j will receive the value of 1 and i the value of 2.


Things go a bit differently here.



int i, j;

i = 1;
j = ++i;

The variable i is assigned with the value of 1; next, the i variable is incremented and is equal to 2; next, the increased value is assigned to the j variable.

In effect, both i and j will be equal to 2.


Look carefully at this program. Let’s trace its execution step by step.



int i, j;

i = 4;
j = 2 * i++;
i = 2 * --j;

The i variable is assigned the value of 4;
We take the original value of i (4), multiply it by 2, assign the result (8) to j and eventually (post-)increment the i variable (it equals 5 now);
We (pre-)decrement the value of j (it equals 7 now); this reduced value is taken and multiplied by 2 and the result (14) is assigned to the variable i.

What else do you need to know about the new operators? Firstly, their priority is quite high – higher than the "*", "/" and "%" operators. Secondly, their binding depends on whether you use the prefix or postfix version. The prefix version operators have a right-to-left binding, while the postfix operators bind from left to right.

Our priority table now reads as follows:

1.3.17 Shortcut operators
Now it's time for the next set of operators, ones that make a developer's life easier. The one’s we’ve already described deal with addition and subtraction of one.



i = i * 2;

However, we often need something other than addition or subtraction, or we want to use a different value; we can use this operator when we want to calculate a series of successive values of powers of 2.

Here’s another example. We use this expression when our herd is extremely numerous:



sheep_counter = sheep_counter + 10;

In the C++ language there is a short way to write these operations. You can write them as follows:



i *= 2;

sheep_counter += 10;

Let's try to present a general description for such operations. If op is a two-argument operator (this is a very important condition!) and the operator is used in the following context:



variable = variable op expression;

then this expression can be simplified as follows:



variable op = expression;

Take a look at the examples here:



Make sure you understand them all. And relax, because we still have a lot of work ahead.

1.3.18   LAB   Parentheses
Level of difficulty
Easy

Objectives
Familiarize the student with:

the order of operations;
the use of parentheses to change the order of operations.
Scenario
Add some parentheses (none, one or two pairs) in the code below to get the expected results. Try to do this before you run the program.


result: 6 expected result : 6
result: 24 expected result : 24
result: 6 expected result : 6
result: 32 expected result : 32
result: 0 expected result : 0
Output

play_arrow
sync
download
light_mode
dark_mode
Console 
terminal
sync
Sample Solution
1.3.19   LAB   Floats: operators and expressions
Objectives
Familiarize the student with:

the concept of integers, floating-point numbers, operators and arithmetic operations in C++ programming;
understanding the precedence and associativity of C++ operators as well as the proper use of parentheses;
performing basic calculations.
Scenario
Take a look at the code in the editor - it reads a float value, puts it into a variable named x and prints the value of a variable named y. Your task is to complete the code in order to evaluate the following expression:




We expect the result to be assigned to y.

Note: we've prepared a variable containing the value of π. Use it.

Be careful! Watch the operators and keep their priorities in mind. Remember that classical algebraic notation likes to omit the multiplication operator – you need to use it explicitly.

Don't hesitate to use as many parentheses as you need. Keep your code clean and readable – surround the operators with spaces.

Use additional variables to shorten the expression.

Hint: multiply x by x to get x squared.

Test your code by using the data we've provided – don't be discouraged by any initial failures. Be persistent and inquisitive. Good luck!

Sample Input
1

Expected output
y = 0.0949234
Output

Sample Input
-1.5

Expected output
y = 0.0890702
Output

Sample Input
12.345

Expected output
y = 0.101057
Output

play_arrow
sync
download
light_mode
dark_mode
Console 
terminal
sync
Sample Solution
1.3.20   LAB   Ints: operators and expressions
Level of difficulty
Easy

Objectives
Familiarize the student with:

shortcut and pre/post increment/decrement operators;
building simple expressions;
translating verbal description into programming language;
testing code using known input and output data.
Scenario
Take a look at the code below: it reads two integer values, manipulates them and finally outputs the k variable. The problem is that the manipulations have been described using natural language, so the code is completely useless now.

We want you to act as an intelligent (naturally!) compiler and to translate the formula into real C++ notation. Try to use pre/post and short-cut operators – they fit perfectly into some of the steps.

Test your code using the data we've provided.


Sample Input
100
3
Expected output
261838
Output
Sample Input
3
100
Expected output
-5
Output
Sample Input
123
321
Expected output
-125
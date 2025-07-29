1.2.1 Numbers and how computers see them
Do you know how computers perform calculations on numbers? Maybe you've heard of the binary system and know that it’s the system computers use for storing numbers and that they can perform any operation upon them. We’re not going to go the intricacies of positional numeral systems here, but we will say that the numbers handled by modern computers are of two types:

integers, that is, those which are devoid of the fractional part;
floating-point numbers (or simply floats), that contain (or are able to contain) the fractional part.
This definition is quite simplistic, but good enough for our purposes. This distinction is very important and the boundary between these two types of numbers is very strict.

Both of these kinds of numbers significantly differ in how they are stored in a computer memory and in the range of acceptable values.

Additionally, the characteristic of a number which determines its kind, range and application is called type.


So now we know two types of the C++ language – an integer type (known as int) and a floating point type (known as float).

For now, let's leave the floating-point numbers aside (that’s right: more on them later) and let’s consider a question that’s maybe a bit banal at first glance: how does the C++ language recognize the integers?

Well, it’s almost the same as when you write them on a piece of paper – they’re simply a string of digits that make up a number. But there’s a catch – you can’t include any characters that are not digits inside the number.

Take for example the number eleven million one hundred and eleven thousand one hundred and eleven. If you took a pencil in your hand right now, you would probably write the number like this:

11,111,111

or (if you are a Pole or a German) like this:

11.111.111

or even like this:

11 111 111

For sure, this makes it easier to read if the number consists of many digits. However, C++doesn’t like this at all. You have to write this number as follows:

11111111

If you don’t, the compiler will shout at you. And how do you code negative numbers in C++? As usual, by adding a minus. You can write:

-11111111

Positive numbers don’t need to be preceded by the plus sign, but you can do it if you want. The following lines describe the same number:

+123

123

For now we’ll deal only with integers – we’ll introduce floating-point numbers very soon.

There are two additional conventions, unknown to the world of mathematics. The first of them allows us to use the numbers in an octal representation. If an integer number is preceded by the 0 digit, it will be treated as an octal value. This means that the number must contain digits taken from the 0 to 7 range only.

0123

is an octal number with a (decimal) value equal to 83.

The second allows us to use hexadecimal numbers. Such number should be preceded by the prefix written as 0x or 0X.

0x123

is a hexadecimal number with the (decimal) value equal to 291.

1.2.2 A variable is variable
So the C++ language allows us to write numbers. It probably won't surprise you that we can do some arithmetic operations with these numbers too: add, subtract, multiply and divide. Contain your excitement – we’ll be doing that soon enough. But it’s quite normal to ask how to store the results of such operations in order to use them in other operations.



There are special "containers" for that purpose and these containers are called variables.

As the name variables suggests, the content of a container can be varied in (almost) any way.

What does every variable have?

a name;
a type;
a value;


Let's start with the issues connected with a variable’s name.

Variables don’t magically appear in our program. We (as developers) decide how many, and which variables, we want to have in our program. We also give them their names, almost becoming their godparents. If you want to give a name to the variable, you have to follow some strict rules:

the name of the variable must be composed of upper-case or lower-case Latin letters, digits and the character _ (underscore);
the name of the variable must begin with a letter;
the underline character is a letter (strange but true);
upper- and lower-case letters are treated as different (a little differently than in the real world – Alice and ALICE are the same given names but they are two different variable names, consequently, two different variables);
These same restrictions apply to all entity names used in C++.

The standard of the C++ language does not impose restrictions on the length of variable names, but a specific compiler may have a different opinion on this matter. Don't worry; usually the limitation is so high that it’s unlikely you would actually want to use such long variable names (or functions).


Here are some correct, but not always convenient variable names:

variable
i
t10
Exchange_Rate
counter
DaysToTheEndOfTheWorld
TheNameOfAVariableWhichIsSoLongThatYouWillNotBeAbleToWriteItWithoutMistakes
_
The last name may be ridiculous from your perspective, but your compiler thinks it’s just great.

And now some incorrect names:

10t (does not begin with a letter)
Adiós_Señora (contains illegal characters)
Exchange Rate (contains a space)
You can find more information about C++ naming style and conventions in the C++ Core Guidelines.

The type is an attribute that uniquely defines which values can be stored inside the variable. We’ve already encountered the integer (int) and floating point (float) types. The value of a variable is what we have put into it. Of course, you can only enter a value that is compatible with the variable’s type. Only an integer value can be assigned to an integer variable (or in other words, to a variable of type int). The compiler will not allow us to enter a floating-point number here.

Let's talk now about two important things – how the variables are created and how to enter a value inside them (or rather – how to give them a value).

The variable exists as a result of a declaration. A declaration is a syntactic structure that binds a name provided by the programmer with a specific type offered by the C++ language. The construction of such a declaration (or the declaration syntax) is simple: just use the name of the desired type, then the variable name (or variable names separated by commas if there are more than one). The whole statement ends with a semicolon.

Let's try to declare a variable of type int named counter. The relevant portion of the program looks like this:



int counter;

What is declared by the following fragment of a program?



int variable_1, account_balance, invoices;

It declares three variables of type int named (respectively) variable_1, account_balance and invoices.

Remember that you are allowed to use as many variable declarations as you need to achieve your goal.


And how do we give a value to the newly declared variable? You need to use the so-called assignment operator. Although this sounds rather mysterious, the operator has a simple syntax and unambiguous interpretation. The assignment operator looks very familiar – here it is:



=

Let's look at some examples:



counter = 1;

The above statement says: assign a value of 1 to a variable named counter or a bit shorter assign 1 to counter.

Some programmers use a different convention and read such a statement as: counter becomes 1.

Another example:



result = 100 + 200;

In this case, the new value of the variable result will be the result of adding 100 to 200, but you probably already guessed that, right?


And now a slightly more difficult example:



x = x + 1;

Seeing that, a mathematician would probably protest – no value may be equal to itself plus one. This is a contradiction.

But in the "C" language the sign "=" does not mean is equal to, but assign a value.

So how do we read such a record in the program?

Take the current value of the variable x, add 1 to it and store the result in the variable x

In effect, the value of variable x was incremented by one, which has nothing to do with comparing the variable to any value.
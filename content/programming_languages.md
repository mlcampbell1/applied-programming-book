# What is a Programming Language

A programming language is a formal language to define **data structures** and **algorithms**. It is used to instruct a machine to perform a well-defined task.
Most languages also provide means to **control the program flow**, that is the order in which the instructions of an algorithm are executed.
The instructions itself are build according to grammar of the programming language, called the **syntax**.

## Data Structure
Data structures are used to organize information in a way that enables efficient access and modification of the data.
A simple example is a floating point number where the respective information is an actual number, such as `1.45`.
A programming language offers a way to store the number and it offers operators on it, e.g. summation and multiplication.
How the number is actually stored in memory and how the operations are performed is hidden away from the programmer.
A floating point number is, in most programming languages, a build-in data type which means that it is readily available to the programmer.
Many programming languages also allow to create new data structures, based on existing ones.
This allows the programmer to design application specific data structures.

## Algorithm
A algorithm is a finite sequence of well-defined instructions to solve a problem or to perform a computation.
The concept of an algorithm is quite old and exists since the antique, e.g. in the form of arithmetic algorithms such as the [Euclidean algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm) to compute the greatest common divisor.
Since the order of execution of the instructions are well-defined, algorithms can be easily implemented in a machine executable way which is one task of the programmer.

### A non-computer example
<a title="Hansmuller / CC BY-SA (https://creativecommons.org/licenses/by-sa/4.0)" href="https://commons.wikimedia.org/wiki/File:Music_box_with_detachable_handle_-_2.jpg">
<img width="256" alt="Music box with detachable handle - 2" src="https://upload.wikimedia.org/wikipedia/commons/f/f8/Music_box_with_detachable_handle_-_2.jpg">
</a>

A non-computer example of a programmable machine is a [music box](https://en.wikipedia.org/wiki/Music_box).
In this case, the algorithm is the roll on which the melody is encoded.
The only data structure available is a pin standing out of the roll.
The tone that is played by the pin is defined by the position of the pin along the direction of rolls' axis.
Hence, the set of all allowable positions form the syntax.
The order of execution (playing of tones) is defined by the relative position of the pins along the direction of rotation of the roll.
Even such a simple machine as the music box offer all fundamental elements of a programming language.

### A computer example

The following is a [Fortran](https://en.wikibooks.org/wiki/Fortran) implementation of [Euclid's algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm) to find the greatest common divisor.
In fact, in the 1960s, Fortran programs where written using punch cards, hence programming was a mechanical exercise in those days, just like for the music box.
Nowadays, Fortan programs are written using a text editor on a computer.

```Fortran
function greatest_common_divisor(A, B) result(gca)
  IMPLICIT NONE
  integer, intent(in) :: A
  integer, intent(in) :: B
  integer             :: gca

  do while (B .ne. 0)
      if (A .gt. B) then
          A = A - B
      else
          B = B - A
      end if
  end do

  gca = A
end function greatest_common_divisor
```

In this example, the algorithm is wrapped into a function that takes two arguments, `A` and `B`, which are of type `integer` (this is how natural numbers are called in computer science).
The value that is returned by the function been given the name `gca`. Can you figure out, what the algorithm is doing?

The above text, called the **source code**, cannot be directly executed by the computer.
First, it must be translated to a machine readable set of instruction.
With Fortran this is done by the **compiler**, a computer program that translates the source code to machine code.
The result is a binary executable, that is a executable file, that is able to run on the machine it has been compiled for.
While the source code can be compiled for many different machines (we also say "architectures"), the binary executable is specific to a single machine.

### Another computer example
Now we take a look at the same algorithm as above, but now it is implemented in [Python](https://www.python.org).

```python
def function(a, b):
    """Find the greatest common divisor of two integer."""
    while b > 0:
        if a > b:
            a = a - b
        else:
            b = b - a
    return a
```

Note that for both, the Fortran and Python example, the algorithm is the same but the implementation is different since both languages are obviously different.
One not so obvious but important difference of both languages is that, unlike Fortran, the Python code does not need to be compiled before the program can be executed.
More precisely, for execution, the source code is read by a program, called the **interpreter**, which executes all the instructions line by line in the order in which they are read.


## Types of Programming Languages

There are different types of programming languages and many ways of distinguishing them.
One possible way of distinction is grouping them into machine or assembler languages, higher programming languages, scripting languages and graphical programming languages.

### Assembler

An Assembler language is a low-level language which instructions have a very strong correspondence to the instructions of the architecture's machine code.
For example, the language contains instructions for moving data from memory to the processor register and to perform operations on it.
Computer architectures differ, hence each architecture has its own machine language and a corresponding assembler language.
A compiler of a high-level language is translating the high-level language code into the machine specific assembler language and from that the executable is build.

Below is some example of assembler code. While the code is hardly readable for a human, it is perfectly readable for a machine.
<a title="BigDumbDinosaur, representing BCS Technology Limited [CC BY-SA 3.0 (https://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:W65C816S_Machine_Code_Monitor.jpeg"><img width="512" alt="W65C816S Machine Code Monitor" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c0/W65C816S_Machine_Code_Monitor.jpeg/512px-W65C816S_Machine_Code_Monitor.jpeg"></a>

### High-level Languages

The aim of high-level languages is to enable a programmer to write code that is more or less independent of the underlying hardware.
Examples of high-level languages are C, FORTRAN or Python.
For compiled languages, such as C or FORTRAN, the code is compiled once by a program called the compiler, which is specific for a particular architecture and operating system.
Hence the same code may be compiled for a Mac OS X, Windows 10 or a GNU Linux machine.
Interpreted languages, such as Python, are read by a program, called the interpreter, every time they are run.
The interpreter is a compiled program which is specific for a particular machine.

By looking at some code example, here in C, we can already get some idea about what the program does.  
```c
#include <stdio.h>
int main()
{
    int number;

    printf("Enter an integer: ");
    scanf("%d", &number);

    // True if the number is perfectly divisible by 2
    if(number % 2 == 0)
        printf("%d is even.", number);
    else
        printf("%d is odd.", number);

    return 0;
}
```

### Scripting Languages

Scripting languages are mostly used to control computers or to automate task using a computer.
In a scripting language the instructions typically consists of processing some data using existing programs.
A scripting language typically also offers some language structures, such as loops and branching, and the possibility of storing data in variables.
This allows to build customized complex functions or tasks which greatly helps in the daily work.

The example below is for bash. In the first line, it lists all files matching some pattern (`ls *_restart_*.nc`), reverses this list (`rev`), split each filename at the underscores and returns everything except the first column (`cut -d_ -f2-`), drop all duplicate lines (`uniq`) and reverses the result again (`rev`).
The output of each of the programs is "piped" to the next one using the pipe operator `|`.
Then the script iterates over the resulting list and for each entry we combine all files matching some pattern into a single archive file (`tar -czvf ${stem}.tar.gz ${stem}_????.nc`) and, if that has been successful, we remove these files (`rm -v ${stem}_????.nc`). These kind of scripts will greatly help if you deal with thousands of files.
```bash
#!/bin/bash

for stem in $(ls *_restart_*.nc |  rev | cut -d_ -f2- | uniq | rev); do
    tar -czvf ${stem}.tar.gz ${stem}_????.nc && rm -v ${stem}_????.nc
done
```

### Graphical Languages

Graphical languages use a visual representation of the program flow or structure.
These type of languages are often used for educational purposes, e.g. as for LEGO Mindstorm.
There also exist visual tools for creating graphical user interfaces (GUI).
There, the GUI elements such as buttons or text fields may listen to events triggered by other elements.
For example if some button is pressed, the "button pressed" event for this particular button is triggered.
A text field listens for this kind of event and changes its text to something else.
This kind of programming model can be visualized and hence, using some tool to draw all the relations, large part of the code can be generated by a computer instead of a human.

<a title="Lehmos [CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0)], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Programm_Wiederhole_Fahre_Drehe.png"><img width="90%" alt="Programm Wiederhole Fahre Drehe" src="https://upload.wikimedia.org/wikipedia/commons/5/5b/Programm_Wiederhole_Fahre_Drehe.png"></a>

## Language Elements

A programming language consists of the following elements: syntax, semantic, type system, and the standard library.  
All these elements determine if the following code is valid and can be executed by the computer.

```python
def add5(x):
    if isinstance(x, int):
        x = x + 5
    else:
        raise TypeError("Wrong type")
    return x

print(add5(64))
```

### Syntax

The *syntax* is the grammar of a language.
It describes all possible combination of symbols (words, numbers, characters) which may make a syntactically correct program.

Here is an example oriented after the language *List*:

```
expression ::= atom | list
atom       ::= number | symbol
number     ::= [+-]?['0'-'9']+
symbol     ::= ['A'-'Z''a'-'z'].*
list       ::= '(' expression* ')'
```
This means, an `expression` is either a `atom` or a `list`.
An `atom` is either a `number` or a `symbol`.
A `number` may be signed and contains a non-zero number of digits.
A `symbol` is any combination of lower- and uppercase letters.
A `list` is surrounded by round brackets and may contain zero or more Elements of the type `expression`.
Hence a `list` may contain a `list` as a n element.

Note that not all syntactically correct programs are correct or make sense.
Here is a natural language example of statements which have a correct grammar but do not make sense.
```
"Colorless green ideas sleep furiously."
"John is a married bachelor."
```

### Semantic

The meaning of a language is described by the *semantic*.
We distinguish between *static semantic* and *dynamic semantic*.

The static semantic defines limitations to the structure of a valid text which cannot be expressed by semantic rules.
Often this is done by defining a *type system* and valid combinations of types.

```Python
def f(x):
    return x
f + 3        # semantically not correct
f(4, 5, 6)   # semantically not correct
```

The dynamic semantic defines how and when the various instructions of a language result in program behavior.
In the Python example below, in the last line `a` and `b` are assigned to `b` and `b+a` in one statement.
```Python
a = 1
b = 2
a, b = b, b + a
```
`b` could have the value `3` or `4`, depending on the meaning of `a` at the end of the last line.
In Python, the semantic rule for assignment operations is that before the assignment, the right hand side is evaluated.
That means that `b` will have the value `3` in the end.

### Type System

A *type system* classifies values and expressions in *types*.
Possible types for a number may be integer, floating point or complex.
Other types might be function, class or exception.
By classifying objects into types, valid operations on combinations of types can be defined.
This can guarantee the correctness of a peace of code.
Not all languages have a type system.
We distinguish languages as

-   *typed* vs *untyped*: untyped languages allow all operations on all kind of data.
    Typed languages only allow for some operations on particular types.
-   *static* vs *dynamic* typing: static typing requires to specify the type of some data before the program is run.
    Dynamic typing checks the correctness of a program while it is executed.
-   *weak* vs *strong* typing: weak typing allows to treat data of one type as being of another compatible type, e.g. by doing implicit type conversion.

The following example is valid Python code.
```Python
def add_one(x):
    return x + 1.0

a = add_one(1)
b = add_one(4.0)
```
We define the function `add_one` but we do not specify the type of the parameter `x`.
We can call the function both with an integer or a floating point number as its argument.
Hence, the language is dynamically typed.
Within the function we add the floating point number `1.0` to the argument and return the result.
For a strongly typed language, additions are only possible for numeric data of the same type.
However, the program has no problem in accepting a integer as the argument to the function.
When the addition is taking place, the integer number is implicitly converted to a float.


## Programming paradigms

A *programming paradigm* is a style of creating the structure and components of a program.
Programming languages may be classified into following paradigms:

-   **declarative**: describes what shall be done but not how (e.g. [SQL](https://en.wikipedia.org/wiki/SQL), [HTML](https://en.wikipedia.org/wiki/html))
    -   *functional*: the result is formulated as a chain of functions (e.g. [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language))
    -   *logical*: the result is the answer to a question about a system of rules and facts (e.g. [Prolog](https://en.wikipedia.org/wiki/Prolog))
    -   *mathematical*: the result is the solution to a optimization problem (e.g. [AMPL](https://en.wikipedia.org/wiki/AMPL))
-   **imperativ**: consists of instructions on how the machine is changing its state
    -   *procedural*: groups instructions into procedures or functions (e.g. [C](https://en.wikipedia.org/wiki/C_(programming_language) or [FORTRAN](https://en.wikipedia.org/wiki/Fortran))
    -   *object-oriented*: groups instructions together with the related data (e.g. [Java](https://en.wikipedia.org/wiki/Java_(programming_language))

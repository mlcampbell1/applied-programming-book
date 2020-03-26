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

## A non-computer example
<a title="Hansmuller / CC BY-SA (https://creativecommons.org/licenses/by-sa/4.0)" href="https://commons.wikimedia.org/wiki/File:Music_box_with_detachable_handle_-_2.jpg">
<img width="256" alt="Music box with detachable handle - 2" src="https://upload.wikimedia.org/wikipedia/commons/f/f8/Music_box_with_detachable_handle_-_2.jpg" class="left">
</a>
A non-computer example of a programmable machine is a [music box](https://en.wikipedia.org/wiki/Music_box).
In this case, the algorithm is the roll on which the melody is encoded.
The only data structure available is a pin standing out of the roll.
The tone that is played by the pin is defined by the position of the pin along the direction of rolls' axis.
Hence, the set of all allowable positions form the syntax.
The order of execution (playing of tones) is defined by the relative position of the pins along the direction of rotation of the roll.
Even such a simple machine as the music box offer all fundamental elements of a programming language.

## A computer example

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

## Another computer example
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


# Types of Programming Languages

-   Maschinensprache und Assemblersprachen: hardwarenahe Programmierung

-   Höhere Programmiersprachen: komfortableres, schnelleres Programmieren

-   Skriptsprachen: Steuerung von Rechnern

-   Grafische Programmiersprachen

## Assembler

<a title="BigDumbDinosaur, representing BCS Technology Limited [CC BY-SA 3.0 (https://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:W65C816S_Machine_Code_Monitor.jpeg"><img width="512" alt="W65C816S Machine Code Monitor" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c0/W65C816S_Machine_Code_Monitor.jpeg/512px-W65C816S_Machine_Code_Monitor.jpeg"></a>

---
## High-level Languages

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
---

## Scripting Languages

```bash
#!/bin/bash

for stem in $(ls *_restart_*.nc |  rev | cut -d_ -f2- | uniq | rev); do
    tar -czvf ${stem}.tar.gz ${stem}_????.nc && rm -v ${stem}_????.nc
done
```
---

## Graphical Languages

<a title="Lehmos [CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0)], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Programm_Wiederhole_Fahre_Drehe.png"><img width="90%" alt="Programm Wiederhole Fahre Drehe" src="https://upload.wikimedia.org/wikipedia/commons/5/5b/Programm_Wiederhole_Fahre_Drehe.png"></a>

---

# Language Elements

```python
def add5(x):
    if isinstance(x, int):
        x = x + 5
    else:
        raise TypeError("Wrong type")
    return x

print(add5(64))
```

-   Syntax

-   Semantik

-   Typen System

-   Standard Library

---
## Syntax

Die *Syntax* is die Grammatik einer Sprache. Sie beschreibt alle möglichen
Kombinationen von Symbolen (Wörter, Zahlen, Zeichen), die ein syntaktisch
korrektes Programm bilden können.

Beispiel angelegt an *List*:

```
expression ::= atom | list
atom       ::= number | symbol
number     ::= [+-]?['0'-'9']+
symbol     ::= ['A'-'Z''a'-'z'].*
list       ::= '(' expression* ')'
```

Nicht alle syntaktisch korrekten Programme sind semantisch korrekt oder sinnvoll:

```
"Colorless green ideas sleep furiously."
"John is a married bachelor."
```
---

## Semantik

Die *Semantik* beschreibt die Bedeutung einer Sprache.

*Statische Semantik*: definiert Beschränkungen der Struktur gültigen Texts, welche
nicht durch semantische Regeln ausgedrückt werden können. Häufig geschieht dies
durch die definition eines *Typen Systems*.

```Python
def f(x):
    return x
f + 3        # semantisch nicht korrekt
f(4, 5, 6)   # semantisch nicht korrekt
```

*Dynamische Semantik*: definiert wie und wann die verschieden Konstrukte einer
Sprache ein Programmverhalten erzeugen.

```Python
a = 1; b = 2
a, b = b, b + a
```

---

## Typen System

Ein *Typen System* definiert, wie eine Programmiersprache Werte und Ausdrücke
in Typen klassifiziert. Dadurch soll die Richtigkeit eines Programms sicher
gestellt werden.

-   *typed* vs *untyped*: untyped Sprachen erlauben jede Operation auf allen Daten.
    Typisierte Sprachen erlauben nur bestimmte Operation zwischen bestimmten Typen.
-   *static* vs *dynamic* typing: bei statisch typisierte Sprachen muss der Type
    vor der Programmausführung definiert werden. Bei dynamisch typisierten Sprachen
    wird die Korrektheit einer Operation zur Laufzeit überprüft.
-   *weak* vs *strong* typing: schwach Typisierung erlaubt, einen Typen wie einen anderen
    zu behandeln, z.B. durch implizite Typenkonversion.

```Python
1.0 + 1
5 / 3
```

---

# Programmierparadigmen

Ein *Programmierparadigma* ist ein Stil um Struktur und Bestandteile eines Programms zu erstellen.
Programmiersprachen können nach folgenden Paradigmen klassifiziert werden:

-   **deklarativ**: beschreibt, was gemacht werden soll, aber nicht wie (z.B. SQL, HTML)
    -   *funktional*: Ergebnis ist formuliert als eine Verkettung von Funktionen
    -   *logisch*: Ergebnis ist formuliert als die Antwort auf eine Frage über ein System von Regeln und Tatsachen
    -   *mathematisch*: Ergebnis ist formuliert als die Lösung eine Optimierungsproblems
-   **imperativ**: besteht aus Anweisungen, wie die Maschine ihren Zustand ändern soll
    -   *prozedural*: gruppiert Instruktionen in Prozeduren
    -   *objektorientiert*: Instruktionen werden zusammen mit dem dazugehörigen Zustand gruppiert.

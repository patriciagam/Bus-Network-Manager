# IAED: Introduction to Algorithms and Data Structures (C)

Lab exercises and two projects written in C for *Introdução aos Algoritmos e Estruturas de Dados* (IAED) at Instituto Superior Técnico. The two projects build a public transport management system, first with fixed-size arrays and then with dynamic memory and linked lists.

## Projects

Both projects manage bus **lines**, **stops** and **links** (a connection between two stops on a line, with a cost and a duration). They read commands from standard input and print results to standard output.

### Project 1: static arrays

Fixed-size arrays hold up to 200 lines and 10,000 stops.

| Command | Action |
| --- | --- |
| `c` | Add a line, or list a line's route (`inverso` lists it in reverse), or list all lines |
| `p` | Add a stop (name, latitude, longitude), or list all stops |
| `l` | Add a link between two stops on a line, with cost and duration |
| `i` | List stops where two or more lines intersect |
| `q` | Quit |

### Project 2: dynamic memory and linked lists

Same system, rewritten with heap allocation. Lines, stops and links are stored in linked lists, so there are no fixed limits. All allocated memory is freed on exit, and an allocation failure is handled with a clean exit.

It adds three commands:

| Command | Action |
| --- | --- |
| `r` | Remove a line |
| `e` | Remove a stop |
| `a` | Remove everything and restart the system |

The code is split into modules: `lines.c`, `stops.c`, `links.c`, with the command loop in `project2.c` and shared types and prototypes in `project2.h`.

## Labs

Weekly exercises, each one a small C program:

| Folder | Topics |
| --- | --- |
| `LAB02` | Basic input and output, conditionals, loops |
| `LAB03` | Character processing and state machines |
| `LAB04`, `LAB05` | Arrays and functions |
| `LAB09` | Structs, dynamic memory, a growable stack with `realloc` |
| `LAB11` | Linked lists: stack, doubly linked list |

`LAB09/ex03.c` and `LAB09/ex04.c` are unfinished and do not compile.

## Build and run

```bash
# Project 1
cd "Projeto 01"
gcc -Wall -ansi -pedantic -o project1 project1.c
./project1 < input.txt

# Project 2
cd "Projeto 02"
gcc -Wall -ansi -pedantic -o project2 project2.c lines.c stops.c links.c
./project2 < input.txt
```

Example session (project 2):

```
p Alpha 1.0 2.0
p Beta 3.0 4.0
c L1
l L1 Alpha Beta 1.5 2.5
c L1
q
```

Output:

```
Alpha, Beta
```


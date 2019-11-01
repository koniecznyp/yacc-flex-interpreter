# yacc-flex-interpreter

``Yacc`` provides a general tool for describing the input to a computer program. The Yacc user specifies the structures of his input, together with code to be invoked as each such structure is recognized. ``Flex`` is a tool for generating scanners: programs which recognized lexical patterns in text.

The above tools have been used to build a simple interpreter to perform mathematical operations. The whole program is based on a user defined ``grammar``, which can be changed as needed. It supports basic mathematical operations such as ``+``, ``-``, ``*`` and ``/`` including the operator precedence. Integer and floating point numbers as well as positive and negative numbers can be used to perform calculations. It is possible to run the exponentiation (``**`` operator) or logarithms (``log`` operator).

This interpreter gives you the option to run the functions. An example is the ``max`` function that returns the largest number of arguments passed as parameters. ``max(5,13,0,55,27)`` returns 55, ``max(2 ** 4, 2 ** 6, 4 ** 3)`` returns 64 and so on.

## Examples
``10 + 2 ** 5 =`` In this case, the exponentiation operation will be performed first. The next operation will be adding and the final result will be 42.

``4 ** ((max(4.25,12,6.9) * 4) / 8) =`` This example shows the possibility of nesting operations. The result will be 4096.

## Setup
You need ``yacc`` and ``flex`` to generate the required files. To download packages, follow the instructions below:
```
apt-get update
apt-get install flex
apt-get install bison
apt-get install libc-dev
```
After downloading the packages, perform the following operations which will generate the following files: ``y.tab.c``, ``y.tab.h`` and ``lex.yy.c``
```
yacc -d parser.y
flex scanner.l
```

Then build an interpreter using ``gcc`` compiler:
```
gcc y.tab.c lex.yy.c -o interpreter -lm
```

## Usage
If everything went well you can run the built program by typing in the terminal
```
./interpreter
```
This will start the program, which will start analyzing the content of the ``data.txt`` file and will perform actions. Each operation saved in the file must end with the operator ``=``. This is information for the interpreter thanks to whom he knows where the instruction entry ends. Inside the ``data.txt`` file it is possible to use multi-line comments using ``/* */`` notation. The content of the comments is not interpreted. The result of each operation will be displayed on separate lines. At the very end of the file there is an ``exit`` instruction which is used for terminating the program.

## Additional information
The tools that were used to create this calculator are also used in the open source ``PostgreSQL`` database. If you would like to deepen your knowledge and if you are interested in implementation please visit 
```
https://github.com/postgres/postgres/tree/master/src/backend/parser
```

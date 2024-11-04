java cProblem 1. Basic knowledge
Problem 2. Polynomial evaluation
Input format
Output format
Example
Notes
Problem 3. GCC argument descriptor
Problem background
Problem description
1. -Wall
2. -Wpedantic
3. -Wextra
4. -Werror
5. -o xxx
6. -I xxx
7. -std=xxx
8. Other
Notes
Example
Problem 4. 6174
Hint
Input format
Output format
Example
Note
Problem 5: CPU emulator
Description
Input format
Output format
Example
Note
Problem 1. Basic knowledge
1. Suppose c is a variable of type char. If c is a decimal digit character, how
can we obtain its numeric value?
int(c)
c - 48
c - '0'
c - '\0'
*(int *)c
2. Regarding undefined behaviors, which of the following statements is/are
true?
An undefined behavior results in one of a set of valid results. For example,
the following code (assuming int is 32-bit) will assign the variable x with
some value, but the value is not valid.
int ival = 10000000;
int x = ival * ival;
An undefined behavior means that there are no restrictions on the behavior
of the program. The standard does not require such programs to do
anything meaningful.
An undefined behavior means that two or more behaviors are permitted by
the standard and that the compiler will choose a meaningful one. The
behavior remains unchanged when the program is run again, although we
don't know what the behavior is.
Correct C programs shall not have undefined behaviors.
3. Suppose int is 32-bit and long long is 64-bit. Select the code snippet(s)
that involve(s) integer overflow.
int x = 42 / 0;
int ival = 1000000;
long long llval = ival * ival;
unsigned uval = -42;
unsigned u1 = 10000000;
unsigned u2 = u1 * u1;
4. Select the code snippet(s) that involve(s) undefined behavior.
int random(void) {
 int x;
 return x;
}
int main(void) {
 printf("%d\n", random());
}
unsigned uval = -5;
printf("%u\n", uval);
int table[100];
int exists_in_table(int value) {
 for (int i = 0; i .
The evaluation of P (xi) at a given point xi
 should be done using only one loop
without call to standard library functions. Think about how to do this efficiently.
Problem 3. GCC argument descriptor
Problem background
To compile C/C++ code, we need to execute a command that calls the compiler
with some arguments. For example:
gcc hello.c -o hello.exe -std=c17 -Wall -Wpedantic -Wextra
This command compiles the C source code file hello.c with gcc, setting the
output file to be hello.exe, setting the language standard to be ISO C17, and
enabling some kinds of warnings and errors by -Wall -Wpedantic -Wextra.
Taking a look at GCC's manual, you will find an overwhelmingly long list of
supported arguments. Is there a tool that can generate some explanations of
the arguments, or at least for some of the most common ones? For example,
suppose the name of that tool is gcc_descriptor.exe (without .exe on Mac OS
X and Linux). It would be helpful if the following command (with .\ replaced by
./ on Mac OS X and Linux)
.\gcc_descriptor hello.c -o hello.exe -std=c17 -Wall -Wpedantic -Wextra
could print
hello.c: C source code as input file.
-o hello.exe: Place the primary output in file hello.exe.
-std=c17: Set the language standard to ISO C17.
-Wall: Enable all the warnings about constructions that some users consider
questionable, and that are easy to avoid (or modify to prevent the warning).
-Wpedantic: Issue all the warnings demanded by strict ISO C and ISO C++ and reject
all programs that use forbidden extensions.
-Wextra: Enable some extra warning flags that are not enabled by -Wall.
Your task is to implement such a tool that generates explanations for some very
common GCC arguments.
Problem description
Write a program that accepts command-line arguments, which are the
arguments that we want to pass to GCC, and print the descriptions for them.
The supported kinds of arguments are as follows.
1. -Wall
Description:
-Wall: Enable all the warnings about constructions that some users consider
questionable, and that are easy to avoid (or modify to prevent the warning).
2. -Wpedantic
Description:
-Wpedantic: Issue all the warnings demanded by strict ISO C and ISO C++ and reject
all programs that use forbidden extensions.
3. -Wextra
Description:
-Wextra: Enable some extra warning flags that are not enabled by -Wall.
4. -Werror
Description:
-Werror: Make all warnings into errors.
5. -o xxx
Description:
-o xxx: Place the primary output in file xxx.
where xxx is replaced by the actual file name (see the example below). Note that
this option consists of two arguments, where the first one is -o and the second
one is the file name.
6. -I xxx
Description:
-I xxx: Add the directory xxx to the list of directories to be searched for header
files during preprocessing.
where xxx is replaced by the actual directory name (see the example below).
Note that this option consists of two arguments, where the first one is -I and
the second one is the directory name.
7. -std=xxx
Description:
-std=xxx: Set the language standard to yyy.
where xxx is replaced by the actual value (see the example below) and yyy is
replaced by the name of the standard according to the following table.
xxx yyy example example output
cN ISO CN c17 ISO C17
c++N ISO C++N c++20 ISO C++20
gnuN GNU dialect of CN gnu11 GNU dialect of C11
gnu++N GNU dialect of C++N gnu++14 GNU dialect of C++14
N consists of two digits. For example, the 2003 ISO C++ standard is named
C++03.
8. Other
Anything that does not match the patterns above is treated as an input file.
Description:
xxx: yyy as input file.
where xxx is replaced by the file name and yyy is replaced by the type of the file
according to the following table.
xxx yyy example
*.c C source code hello.c
*.h C/C++ header file stdio.h
*.cpp, *.C, *.cc, *.cxx C++ source code checker.cc, game.cpp
*.hpp, *.hxx C++ header file utils.hpp
Notes
There is no input for this problem. The arguments to be explained are given as
the command line arguments of your program.
It is guaranteed that the arguments are valid: Anything that does not match the
patterns in 1 ~ 7 must be a valid C/C++ source or header file name as described
in the table above. For the language standards (pattern 7), you don't need to
check whether the standard that it refers to actually exists. Things like -
std=c++100000 won't appear.
The names of the files and directories involved in the arguments do not contain
whitespaces or quotes.
The name following -o or -I is not a C/C++ source or header file.
Print the explanations in order of the arguments.
Please be extremely careful about the output contents, especially the
spaces, newlines and punctuations.
Example
Suppose the name of your program (executable) is my_program.exe (without
.exe on Mac OS X and Linux). If the following command (with .\ replaced by ./
on Mac OS X and Linux) is executed,
.\my_program -std=c++20 -Wall -Wpedantic -Wextra a.c b.hxx c.cpp -Werror -o
output_file -I /usr/local/boost_1_80_0/
the output is
-std=c++20: Set the language standard to ISO C++20.
-Wall: Enable all the warnings about constructions that some users consider
questionable, and that are easy to avoid (or modify to prevent the warning).
-Wpedantic: Issue all the warnings demanded by strict ISO C and ISO C++ and reject
all programs that use forbidden extensions代 写program、C++
代做程序编程语言.
-Wextra: Enable some extra warning flags that are not enabled by -Wall.
a.c: C source code as input file.
b.hxx: C++ header file as input file.
c.cpp: C++ source code as input file.
-Werror: Make all warnings into errors.
-o output_file: Place the primary output in file output_file.
-I /usr/local/boost_1_80_0/: Add the directory /usr/local/boost_1_80_0/ to the list
of directories to be searched for header files during preprocessing.
Problem 4. 6174
The number 6174 is known as Kaprekar's constant after the Indian
mathematician D. R. Kaprekar. This number is renowned for the following rule:
1. Take any four-digit number, using at least two different digits (leading zeros
are allowed).
2. Arrange the digits in descending and then in ascending order to get two
four-digit numbers, adding leading zeros if necessary.
3. Subtract the smaller number from the bigger number.
4. Go back to step 2 and repeat.
The above process, known as Kaprekar's routine, will always reach its fixed point,
6174, in at most 7 iterations. Once 6174 is reached, the process will continue
yielding 7641 − 1467 = 6174. For example, choose 1459:
Write a program that simulates this process. Note that
The input number should not contain more than 4 digits and should
contain at least two different digits (i.e. not a repdigit like , , ...).
These numbers are said to be invalid.
The input number may contain less than 4 digits. For example, start with :
Hint
The functions given in [Problem 1] Basic knowledge may be helpful for this
problem.
Input format
On the first line, a nonnegative integer .
Then lines follow, the -th of which contains a nonnegative integer . It is
guaranteed that is representable by int.
Output format
For each of the input integers, either report that it is invalid or simulate the
Kaprekar's routine and print the steps (see below).
If for some the integer contains more than 4 digits, print xxx contains more
than 4 digits. where xxx is replaced with . If contains no more than 4
9541
8820
8532
− 1459
− 288
− 2358
= 8082
= 8532
= 6174
1111 2222
9
9000
9981
8820
8532
− 9
− 1899
− 288
− 2358
= 8991
= 8082
= 8532
= 6174
n
n i xi
xi
n
i xi
xi xi
digits but is a repdigit, print xxx is a repdigit. where xxx is replaced with xi
.
A step in the Kaprekar's routine should be printed in the form xxx - yyy = zzz,
where xxx, yyy and zzz are replaced with the corresponding numbers. Note that
leading zeros are not printed (see the example below). The process stops when
zzz reaches 6174.
If the input is already 6174, you should print nothing and start processing next
input.
You don't have to start printing after all inputs are consumed! Do not waste
efforts saving the things to be printed.
Example
Input
5
123456
0
22
4444
1459
Output
123456 contains more than 4 digits.
0 is a repdigit.
2200 - 22 = 2178
8721 - 1278 = 7443
7443 - 3447 = 3996
9963 - 3699 = 6264
6642 - 2466 = 4176
7641 - 1467 = 6174
4444 is a repdigit.
9541 - 1459 = 8082
8820 - 288 = 8532
8532 - 2358 = 6174
Note
Your program will not be compiled and linked against the math library, so
do not use the functions in .
Problem 5: CPU emulator
Description
To understand how the computer executes your program, let me give a short
introduction to CPU. The CPU basically contains 2 parts: registers and ALU. You
can consider registers as an array. Each cell of this array has a name (for
example, x0, x1, x2, …, x31 in RISC-V), and can store a single number. Arithmetic
calculations (addition, subscription, multiplication, division, ...) are done by ALU.
When executing your program, the assembly codes (written in binary) are sent
to CPU. Each line of assembly code specifies some operation of registers, and
CPU will use a special register named PC (program counter) to identify the
current execution line number. For example, if the code is add x3 x1 x2, then
CPU will take the values in registers x1 and x2, add them up and store the result
in the register x3. This is shown in the figure below (only 5 registers shown here).
Then, the CPU increments PC by 1 to execute the next instruction.
In this problem, you are required to implement a toy emulator which is able to
execute a very simple assembly language (similar to RISC-V). You only need to
consider 6 registers, named x0, x1, x2, x3, x4 and x5, all in lowercase, and each
register stores a 16-bit integer. The x0 register is a special one, whose value is
always zero. Also, there are only has 6 instructions in this assembly language:
add, sub, mul, div, let and print, which are introduced below.
In this problem, we use a 16-bit machine code. An example of a 16-bit
instruction is as follows.
The instructions add, sub, mul and div are similar. The syntax is shown in the
following table. Note that in these operations, the imm part is discarded.
Instruction Syntax Explanation OpCode
add add r1 r2 value in r1 += value in r2 000
sub sub r1 r2 value in r1 -= value in r2 001
mul mul r1 r2 value in r1 *= value in r2 010
div div r1 r2 value in r1 /= value in r2 011
The let instruction is used to assign value to a register. The syntax is:
Instruction Syntax Explanation OpCode
let let r1 imm value in r1 = imm 100
where r1 is the name of some register (x0 to x5), and imm is an integer within the
range . In this instruction, the r2 part is discarded and the imm part is
used. For example, the execution of instruction let x1 80 is shown below.
Also, we need a print instruction to print the value in some register so that we
can test whether the execution result is correct. For example, if the value in
register x1 is 5, your emulator should print x1 = 5 on the screen when the
instruction print x1 is executed. The r2 part is also discarded in this instruction.
Instruction Syntax Explanation OpCode
print print r1 print value in r1 101
[0, 2
7 − 1]
Notes:
1. In the div instruction, the division result is truncated towards zero, and the
denominator will always be non-zero.
2. Value in all registers should be initialized to 0 before execution.
3. Remember that the value in x0 is always zero. Any instruction that attempts
to modify it should have no effect.
4. We only consider unsigned immediate in this problem.
Input format
The first line of the input is a number n, indicating the total lines of code.
The following n lines are the instructions written in hexadecimal.
Output format
Your emulator should execute the input program, and only print the result
when a print instruction is executed. It is guaranteed that the input and
output are both non-empty.
Example
Input:
2
0x8401
0xA400
Output:
x1 = 1
Input:
10
0x8401
0x8801
0x8C01
0x9001
0x9401
0xA400
0xA800
0xAC00
0xB000
0xB400
Output:
x1 = 1
x2 = 1
x3 = 1
x4 = 1
x5 = 1
Explanation:
0x8401 is 1000010000000001 in binary, whose opcode is 100, r1 is 001 (x1), r2
is 000 (x0) and imm is 0000001 (1). From the opcode we know that this is a
let instruction, so the instruction is let x1 1.
0xA400 is 1010010000000000 in binary, whose opcode is 101 and r1 is 001
(x1). This is a print instruction, so the instruction is print x1.
Note
Your program will not be compiled and linked against the math library, so
do not use the functions in .

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com

this project is about shell init files ,variables and expansion.
expansions
Pathname Expansion
The mechanism by which wildcards work is called pathname expansion.
example ls ,echo D* ,echo *s, echo [[:upper:]]*, echo /usr/*/share
Tilde Expansion
As we recall from our introduction to the cd command, the tilde character (“~”) has a special meaning. When used at the beginning of a word, it expands into the name of the home directory of the named user, or if no user is named, the home directory of the current user:
echo ~ ,echo~foo
Arithmetic Expansion
The shell allows arithmetic to be performed by expansion. This allow us to use the shell prompt as a calculator:
Arithmetic expansion uses the form:

$((expression))
Brace Expansion
Perhaps the strangest expansion is called brace expansion. With it, we can create multiple text strings from a pattern containing braces. Here's an example:echo Front-{A,B,C}-Back ,
an example using a range of integers:
echo Number_{1..5},

A range of letters in reverse order:
echo {Z..A} , 

Brace expansions may be nested:
echo a{A{1,2},B{3,4}}b
Parameter Expansion
We're only going to touch briefly on parameter expansion in this lesson, but we'll be covering it more later. It's a feature that is more useful in shell scripts than directly on the command line. Many of its capabilities have to do with the system's ability to store small chunks of data and to give each chunk a name. Many such chunks, more properly called variables, are available for our examination. For example, the variable named “USER” contains our user name.

echo $USER

Command Substitution
Command substitution allows us to use the output of a command as an expansion:
echo $(ls)
A clever one goes something like this:
ls -l $(which cp)

Quoting
Double Quotes
The first type of quoting we will look at is double quotes. If we place text inside double quotes, all the special characters used by the shell lose their special meaning and are treated as ordinary characters. The exceptions are “$”, “\” (backslash), and “`” (back- quote). This means that word-splitting, pathname expansion, tilde expansion, and brace expansion are suppressed, but parameter expansion, arithmetic expansion, and command substitution are still carried out. 

Single Quotes
When we need to suppress all expansions, we use single quotes. Here is a comparison of unquoted, double quotes, and single quotes:
Escaping Characters
Sometimes we only want to quote a single character. To do this, we can precede a character with a backslash, which in this context is called the escape character. Often this is done inside double quotes to selectively prevent an expansion:

Shell Arithmetic

The shell allows arithmetic expressions to be evaluated, as one of the shell expansions or by using the (( compound command, the let builtin, or the -i option to the declare builtin.
id++ id--
variable post-increment and post-decrement

++id --id
variable pre-increment and pre-decrement

- +
unary minus and plus

! ~
logical and bitwise negation

**
exponentiation

* / %
multiplication, division, remainder

+ -
addition, subtraction

<< >>
left and right bitwise shifts

<= >= < >
comparison

== !=
equality and inequality

&
bitwise AND

^
bitwise exclusive OR

|
bitwise OR

&&
logical AND

||
logical OR

expr ? expr : expr
conditional operator

= *= /= %= += -= <<= >>= &= ^= |=
assignment

expr1 , expr2
comma


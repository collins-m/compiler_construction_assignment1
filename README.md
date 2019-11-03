# CA4003 Assignment 1

_Assignment found [here]( https://www.computing.dcu.ie/~davids/courses/CA4003/CA4003_assign.html#assignment_1 )._

non-generated file: "javaccFrontEnd.jj"



## Description of the program



### Creating the class

The first section involves defining the parser class. We define how it will be used to parse documents and how it will handle errors here.



### Defining the tokens

The next section defines a set of tokens for the parser to recognise. These are split into three definitions: keywords, punctuation, and numbers/identifiers. The first of these three groups are built-in words used by the language, the second are things such as apostrophes and braces, and the last group is filled with numbers (which are positive and negative whole numbers) and identifiers (strings of characters with possible numbers at the end).



### Managing whitespace and comments

The next step focuses on dealing with whitespace and comments in the file, as they are not interpreted by the parser. This includes things such as tabs, and newline characters too. Comments are dealt with slightly differently, as there are two types. There are single line comments denoted by __"//"...__ and multiline comments encased within __"/\*...\*/__. The former of which can be nested, because of this the parser recursively steps through these nested comments while keeping track of how many layers deep it has travelled.



### Parsing the program

Now with token definitions and ignored characters out of the way, the next section focuses on carrying out the parsing. The first method is defined a list of declarations, followed by a list of functions, the main function, and finally an end of file declaration.

The declaration list is defined as zero or more declarations, each of which is followed by a semicolon. A declaration is defined as a variable or a constant. These are in turn have their own definitions that make use of a _type_ declaration and an _expression_ declaration. Type denotes whether a declaration is an integer, boolean, or void. Expression will be explained further on.

The function list is defined as zero or more functions. They make use of other definitions that I have discussed above while also bringing in some new ones, namely, _parameter lists_ and _statement blocks_. The main function makes use of declaration lists outlined above, and _statement blocks_.

The parameter list Is comprised of zero or more parameters. These parameters make use of the type definition once again. The statement block is a series of zero or more statements, where a statement can be defined by a group of things, including while blocks, and if/else blocks. Several of these definitions are implemented recursively. New definitions that are mentioned here are _argument lists_, _conditions_, and _expressions_.

An expression can be either a _fragment_, or a _binary arithmetic operation_ enacted upon two fragments. This definition may also be encased in parentheses. Binary arithmetic operations are simply plus and minus signs, while a fragment can be the positive or negative of zero or one _argument lists_, followed by a _fragment prime_. It may also be a number, or true, or false, followed by a _fragment prime_.

An argument list is zero or more identifiers, defined recursively. The fragment prime mentioned above is separated from the fragment definition as only a portion of the declaration is to be recursively repeated. This repetition is of zero or more binary arithmetic operations followed by another expression.

Conditions can be defined as one or more fragments followed by _comparative operations_. If there are multiple, they are joined by AND/OR logic. They may also be encased in parentheses or preceded by a tilde. It makes use of _condition prime_ for recursion uses. Comparative operations are things such as equivalence, less than, greater than etc.


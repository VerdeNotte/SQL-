# Data Types for Data Science:

The 4 common data types:

* Numbers (245.3)
* Text ("Goodbye")
* Dates (1991-04-03)
* Logical (True or False)

You can test for different types of data using functions that begin with `IS`

Copying forumlas between cells - Handy trick
Copy right: use CTRL + R
Copy Down: use CTRL + D

Formatting numbers: cell address as their only inputs
A1: 3.45
* `TO_DOLLARS(A1)`Converts the cell to $3.45
*  `TO_PERCENT(A1)` Converts the cell to 345%

Text to number
* `=N `
Can also convert Logicals:
*  True to 1
* False to 0 

Converting units of numbers:
Takes 3 arguments 
*`CONVERT (cell containing the number, existing unit of that number, the unit that you would like to convert to)` - the two units are written inside " ".

Summary:
* `TO()` function format numbers
* `N()` changes text to numbers
* `IF(logical 1,0)` changes logical to numbers
* `Convert()` changes the unit of a number

## Common Data Transformations
### Logarithms & Exponents

If the data contains some values millions or billions times larger than other values, you can use logarithms to make things easier to read.

Logarithms:
How many 3s do we multiply to get 81?
3 x 3 x 3 x3= 81, logarithm is 4
 log<sub>3</sub>81 =4
The number we multiply is called the "base", so we can say:

-   "the logarithm of 81 with base of 3 is 4"
-   or "log base 3 of 81 is 4"
-   or "the base-3 log of 81 is 4"
 Notice we are dealing with three numbers:

-   the  **base**: the number we are multiplying (a "3" in the example above)
-   how often to use it in a multiplication (4 times, which is the  **logarithm**)
-   The number we want to get (an "81")

Exponents:
The exponents says how many times to use the number in a multiplication 
3<sup>4</sup> = 81

The logarithm tells us what the exponent is 

Common Logarithms: Base 10

Natural Logarithm: Base "e"
Base on Euler's number which is about 2.71828

Logarithms can have decimals 
Negative Logarithms
* A negative logarithms means how many times *to divide* by the number
log<sup>8</sup>(0.125)
Well,  1 ÷ 8 = 0.125,
So  log8(0.125) = −1

Logarithmic transformations

* `LOG10()`base 10 log of your number, returns the 10 to the power of that number
* `LN()` - Takes the natural logarithm of a number, -log with base e

Exponential transformations (Undo logarithmic transformations)
* `10 ^`
* `EXP ()`this undoes `LN()` 

Square root transformations
* `SQRT()`

### Rounding and Formatting numbers:

Round: 2 arguments
* ROUND(<sub>X,N</sub>) Rounds <sub>X</sub>  to the nearest <sub>N</sub> decimal place

Ceiling: 2 arguments
* CEILING (<sub>X,Y</sub>) Rounds <sub>X</sub> up to the nearest multiple of <sub>Y</sub>
* will round negative numbers towards or away from negative infinity

Floor: 
* FLOOR (<sub>X,Y</sub>) Rounds <sub>X</sub> down to the nearest multiple of <sub>Y</sub>
* will round negative numbers towards or away from negative infinity

Google Sheets has two related functions called  `FLOOR.MATH()`  and  `CEILING.MATH()`. When given one or two arguments, they behave in the same way as  `FLOOR()`  and  `CEILING()`respectively. However, you can pass the value  `1`  to a third argument to make them round towards or away from zero.

That is,  `FLOOR.MATH(-1.5, , 1)`  is  `-1`  and  `CEILING.MATH(-1.5, , 1)`  is  `-2`.

### Generating random number
An important idea in stats is simulation. There are two functions available for generating numbers from a uniform distribution. In a continuous uniform distribution, any number within a range is likely to be generated. In a discrete uniform distribution, any one of a finite number of values is equally likely to be generated.

Uniform random numbers:
* `RAND()` - between 0 and 1, without any arguments

* `RANDBETWEEN (lowerlimit, upperlimit)` - Always returns intergers

Generate normal random distributed numbers (Also caused Gaussian distribution)
* `NORMINV(RAND(), 0,1` Pass Rand to Norminv. 2nd and 3rd arguments of Norminv is the mean and standard distribution.
There are many other inverse cumulative distribution functions available: you can repeat that same code swapping `FINV()`for the F distribution, `BETAINV()` for the beta distribution, and so on.

### Logical Values
The opposite of true

`NOT()` Swaps TRUE and FALSE

Two logical operations that accept multiple inputs.
`AND()` - all true = true
`OR()` - True when any inputs are True or False when any inputs are False

You can combine the logical operations.

`=AND(C2,  D2,  NOT(E2))`
`=OR(NOT(A2),  B2)`

Flow Control:
Computer science term for running different code until different decisions
Basic principles - if some condition happens do something otherwise do something else

If this then that
`IF` - 3 arguments

Dealing with lots of conditions.

* You can start nesting `IF` functions (can get messy)
* `IFS` - let's you test for as many conditions as you like. It takes pairs of arguments as follows.

Transforming categorical variables 
`SWITCH()`
Combining `IF` and `AND`
`=IF(AND(C2,  D2),  "status1",  "status2")`
Don't forget to wrap the second and third argument in quotes.
Combing If, Not and And

`=IFS(E3,  "young",  NOT(D3),  "none",  AND(D3,  NOT(E3)),  "old")`

### Blanks, missing values and errors
Calculating with blanks will give a wrong answer. It will pretend blanks are 0
Solution to getting correct calculation is to convert the blank into a missing value #N/A

Some calculations involving blank values may give different results to what you might expect. For example, when you pass a blank value into the `AND()` function, it is treated as `TRUE`. This is often unhelpful. To make blanks behave in a sensible way in calculations, you must first convert them to be "not available" using [`NA()`](https://support.google.com/docs/answer/3093359). This function takes no inputs, and returns a missing value. To convert a blank value to a missing value, use this pattern.

`=IF(ISBLANK(cell,NA(),cell)`

Errors
You can test for errors using the `ISERROR()` 
Blank errors isn't consider an error but the missing value is 
`ISERR()` also test for errors as cells but doesn't consider missing values to be errors

Types of errors:

|Error| Cause|
|----|-----|
|#DIV/0!| Dividing by zero|
|#Value| Nonsense data in a calculation|
|#REF| Referencing a cell that has been deleted|
|#NAME?| Forgetting to quote a string|
|#NUM!| Numbers being out of range|
|#N/A| Missing value|
|#ERROR!| Syntax problem in a formula|
|#PARSE|The formula not being formatted correctly|

### Cell Address: 
There are two ways of specifying a cell address:

A1 = format
Some functions require us to think about the row and column number

`ROW` as row number (integer)
`COLUMN` as column number (integer)

`ADDRESS(cell, cell)` `$cell$cell` -Returns an absolute address
4 different return format
relative address
`ADDRESS(cell, cell,4)` `cellcell`

Indirection: 
A computer science term instead of passing a value to the function, you pass the address.

*Example*

* 25 in cell   a2, 25 is the value
`ADDRESS` turns it into an absolute address  $A$2
`INDIRECT` returns it back into the value

Finding nearby cells:
`OFFSET cell,down, right`
You can use negative numbers to go to go up or left from the cell.
0 keeps it at that cell reference

Retrieves the values in cells offset from the current location by a certain number of rows and columns. It takes two arguments: the number of rows down to move from the current location, and the number of columns to move right.

`SUM(OFFSET())` - Combines sum and offset
`=SUM(OFFSET(A3,  0,  2,  7,  1))`

### Relative Address

If your data set doesn't start at the top left of the spreadsheet it is sometimes easier to specify cells relative to the top left of the data set
`INDEX(range of data, row, column)`
range of data should be an absolute address

If you ask for a cell outside of the range it will cause an error.

## Lookup & Matching

#### Left join with VLOOKUP 
Takes 4 arguments
Id column with common values

* 1st argument: Value we want to match
* 2nd argument: Data range usually an absolute address. The first column must contain the lookup values.
* 3rd argument: Column offset. The column for the value to be merged in 
* 4th argument: Whether the data is sorted by the lookup column. Usually false

#### Grammatically sorting data
`=SORT(absolute address range, 2, FALSE)`
* 1st argument:  range not including the header row
* 2nd argument:  number of columns to sort by
* 3rd argument: TRUE sorts in ascending order, FALSE in descending order
#### Matching values

`=MATCH()`
Lets you find values in a osrted data set
Takes 3 arguments
1. is the value to find
2. absolute address of the column of data
3. 1 -descending order, - 1 descending order

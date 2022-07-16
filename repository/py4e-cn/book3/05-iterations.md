
Iteration
=========

\index{iteration}

Updating variables
------------------

\index{update}
\index{variable!updating}

A common pattern in assignment statements is an assignment statement
that updates a variable, where the new value of the variable depends on
the old.

~~~~ {.python}
x = x + 1
~~~~

This means "get the current value of `x`, add 1, and then
update `x` with the new value."

If you try to update a variable that doesn't exist, you get an error,
because Python evaluates the right side before it assigns a value to
`x`:

~~~~ {.python}
>>> x = x + 1
NameError: name 'x' is not defined
~~~~

Before you can update a variable, you have to
*initialize* it, usually with a simple assignment:

\index{initialization (before update)}

~~~~ {.python}
>>> x = 0
>>> x = x + 1
~~~~

Updating a variable by adding 1 is called an *increment*;
subtracting 1 is called a *decrement*.

\index{increment}
\index{decrement}

The `while` statement
--------------------------------

\index{statement!while}
\index{while loop}
\index{loop!while}
\index{iteration}

Computers are often used to automate repetitive tasks. Repeating
identical or similar tasks without making errors is something that
computers do well and people do poorly. Because iteration is so common,
Python provides several language features to make it easier.

One form of iteration in Python is the `while` statement.
Here is a simple program that counts down from five and then says
"Blastoff!".

~~~~ {.python}
n = 5
while n > 0:
    print(n)
    n = n - 1
print('Blastoff!')
~~~~

You can almost read the `while` statement as if it were
English. It means, "While `n` is greater than 0, display the
value of `n` and then reduce the value of `n` by
1. When you get to 0, exit the `while` statement and display
the word `Blastoff!`"

\index{flow of execution}

More formally, here is the flow of execution for a `while`
statement:

1.  Evaluate the condition, yielding `True` or
    `False`.

2.  If the condition is false, exit the `while` statement and
    continue execution at the next statement.

3.  If the condition is true, execute the body and then go back to step
    1.

This type of flow is called a *loop* because the third
step loops back around to the top. We call each time we execute the body
of the loop an *iteration*. For the above loop, we would
say, "It had five iterations", which means that the body of the loop was
executed five times.

\index{condition}
\index{loop}
\index{body}

The body of the loop should change the value of one or more variables so
that eventually the condition becomes false and the loop terminates. We
call the variable that changes each time the loop executes and controls
when the loop finishes the *iteration variable*. If there
is no iteration variable, the loop will repeat forever, resulting in an
*infinite loop*.

Infinite loops
--------------

An endless source of amusement for programmers is the observation that
the directions on shampoo, "Lather, rinse, repeat," are an infinite loop
because there is no *iteration variable* telling you how
many times to execute the loop.

\index{infinite loop}
\index{loop!infinite}

In the case of `countdown`, we can prove that the loop
terminates because we know that the value of `n` is finite,
and we can see that the value of `n` gets smaller each time
through the loop, so eventually we have to get to 0. Other times a loop
is obviously infinite because it has no iteration variable at all.

"Infinite loops" and `break`
---------------------------------------

\index{break statement}
\index{statement!break}

Sometimes you don't know it's time to end a loop until you get half way
through the body. In that case you can write an infinite loop on purpose
and then use the `break` statement to jump out of the loop. ^cdc34e

This loop is obviously an *infinite loop* because the
logical expression on the `while` statement is simply the
logical constant `True`:

~~~~ {.python}
n = 10
while True:
    print(n, end=' ')
    n = n - 1
print('Done!')
~~~~

If you make the mistake and run this code, you will learn quickly how to
stop a runaway Python process on your system or find where the power-off
button is on your computer. This program will run forever or until your
battery runs out because the logical expression at the top of the loop
is always true by virtue of the fact that the expression is the constant
value `True`.

While this is a dysfunctional infinite loop, we can still use this
pattern to build useful loops as long as we carefully add code to the
body of the loop to explicitly exit the loop using `break`
when we have reached the exit condition.

For example, suppose you want to take input from the user until they
type `done`. You could write:

\VerbatimInput{../code3/copytildone1.py}

The loop condition is `True`, which is always true, so the
loop runs repeatedly until it hits the break statement.

Each time through, it prompts the user with an angle bracket. If the
user types `done`, the `break` statement exits the
loop. Otherwise the program echoes whatever the user types and goes back
to the top of the loop. Here's a sample run:

~~~~
> hello there
hello there
> finished
finished
> done
Done!
~~~~

This way of writing `while` loops is common because you can
check the condition anywhere in the loop (not just at the top) and you
can express the stop condition affirmatively ("stop when this happens")
rather than negatively ("keep going until that happens.").

Finishing iterations with `continue`
-----------------------------------------------

\index{continue statement}
\index{statement!continue}

Sometimes you are in an iteration of a loop and want to finish the
current iteration and immediately jump to the next iteration. In that
case you can use the `continue` statement to skip to the next
iteration without finishing the body of the loop for the current
iteration.

Here is an example of a loop that copies its input until the user types
"done", but treats lines that start with the hash character as lines not
to be printed (kind of like Python comments).

\VerbatimInput{../code3/copytildone2.py}

Here is a sample run of this new program with `continue`
added.

~~~~ 
> hello there
hello there
> # don't print this
> print this!
print this!
> done
Done!
~~~~

All the lines are printed except the one that starts with the hash sign
because when the `continue` is executed, it ends the current
iteration and jumps back to the `while` statement to start
the next iteration, thus skipping the `print` statement. ^077021

Definite loops using `for` 
--------------------------------------

\index{for statement}
\index{statement!for}

Sometimes we want to loop through a *set* of things such
as a list of words, the lines in a file, or a list of numbers. When we
have a list of things to loop through, we can construct a *definite*
loop using a `for` statement. We call the `while`
statement an *indefinite* loop because it simply loops until some
condition becomes `False`, whereas the `for` loop
is looping through a known set of items so it runs through as many
iterations as there are items in the set.

The syntax of a `for` loop is similar to the
`while` loop in that there is a `for` statement
and a loop body:

~~~~ {.python}
friends = ['Joseph', 'Glenn', 'Sally']
for friend in friends:
    print('Happy New Year:', friend)
print('Done!')
~~~~

In Python terms, the variable `friends` is a list^[We will examine lists 
in more detail in a later chapter.] of
three strings and the `for` loop goes through the list and
executes the body once for each of the three strings in the list
resulting in this output:

~~~~ {.python}
Happy New Year: Joseph
Happy New Year: Glenn
Happy New Year: Sally
Done!
~~~~

Translating this `for` loop to English is not as direct as
the `while`, but if you think of friends as a
*set*, it goes like this: "Run the statements in the body
of the for loop once for each friend *in* the set named friends."

Looking at the `for` loop, *for* and
*in* are reserved Python keywords, and
`friend` and `friends` are variables.

~~~~ {.python}
for friend in friends:
    print('Happy New Year:', friend)
~~~~

In particular, `friend` is the *iteration
variable* for the for loop. The variable `friend`
changes for each iteration of the loop and controls when the
`for` loop completes. The *iteration variable*
steps successively through the three strings stored in the
`friends` variable.

Loop patterns
-------------

Often we use a `for` or `while` loop to go through
a list of items or the contents of a file and we are looking for
something such as the largest or smallest value of the data we scan
through.

These loops are generally constructed by:

-   Initializing one or more variables before the loop starts

-   Performing some computation on each item in the loop body, possibly
    changing the variables in the body of the loop

-   Looking at the resulting variables when the loop completes

We will use a list of numbers to demonstrate the concepts and
construction of these loop patterns.

### Counting and summing loops

For example, to count the number of items in a list, we would write the
following `for` loop:

~~~~ {.python}
count = 0
for itervar in [3, 41, 12, 9, 74, 15]:
    count = count + 1
print('Count: ', count)
~~~~

We set the variable `count` to zero before the loop starts,
then we write a `for` loop to run through the list of
numbers. Our *iteration* variable is named
`itervar` and while we do not use `itervar` in the
loop, it does control the loop and cause the loop body to be executed
once for each of the values in the list.

In the body of the loop, we add 1 to the current value of
`count` for each of the values in the list. While the loop is
executing, the value of `count` is the number of values we
have seen "so far".

Once the loop completes, the value of `count` is the total
number of items. The total number "falls in our lap" at the end of the
loop. We construct the loop so that we have what we want when the loop
finishes.

Another similar loop that computes the total of a set of numbers is as
follows:

~~~~ {.python}
total = 0
for itervar in [3, 41, 12, 9, 74, 15]:
    total = total + itervar
print('Total: ', total)
~~~~

In this loop we *do* use the *iteration variable*.
Instead of simply adding one to the `count` as in the
previous loop, we add the actual number (3, 41, 12, etc.) to the running
total during each loop iteration. If you think about the variable
`total`, it contains the "running total of the values so
far". So before the loop starts `total` is zero because we
have not yet seen any values, during the loop `total` is the
running total, and at the end of the loop `total` is the
overall total of all the values in the list.

As the loop executes, `total` accumulates the sum of the
elements; a variable used this way is sometimes called an
*accumulator*.

\index{accumulator!sum}

Neither the counting loop nor the summing loop are particularly useful
in practice because there are built-in functions `len()` and
`sum()` that compute the number of items in a list and the
total of the items in the list respectively.

### Maximum and minimum loops

\index{loop!maximum}
\index{loop!minimum}
\index{None special value}
\index{special value!None}

To find the largest value in a list or sequence, we
construct the following loop:

~~~~ {.python}
largest = None
print('Before:', largest)
for itervar in [3, 41, 12, 9, 74, 15]:
    if largest is None or itervar > largest :
        largest = itervar
    print('Loop:', itervar, largest)
print('Largest:', largest)
~~~~

When the program executes, the output is as follows:

~~~~
Before: None
Loop: 3 3
Loop: 41 41
Loop: 12 41
Loop: 9 41
Loop: 74 74
Loop: 15 74
Largest: 74
~~~~

The variable `largest` is best thought of as the "largest
value we have seen so far". Before the loop, we set `largest`
to the constant `None`. `None` is a special
constant value which we can store in a variable to mark the variable as
"empty".

Before the loop starts, the largest value we have seen so far is
`None` since we have not yet seen any values. While the loop
is executing, if `largest` is `None` then we take
the first value we see as the largest so far. You can see in the first
iteration when the value of `itervar` is 3, since
`largest` is `None`, we immediately set
`largest` to be 3.

After the first iteration, `largest` is no longer
`None`, so the second part of the compound logical expression
that checks `itervar > largest` triggers only when we see a
value that is larger than the "largest so far". When we see a new "even
larger" value we take that new value for `largest`. You can
see in the program output that `largest` progresses from 3 to
41 to 74.

At the end of the loop, we have scanned all of the values and the
variable `largest` now does contain the largest value in the
list.

To compute the smallest number, the code is very similar with one small
change:

~~~~ {.python}
smallest = None
print('Before:', smallest)
for itervar in [3, 41, 12, 9, 74, 15]:
    if smallest is None or itervar < smallest:
        smallest = itervar
    print('Loop:', itervar, smallest)
print('Smallest:', smallest)
~~~~

Again, `smallest` is the "smallest so far" before, during,
and after the loop executes. When the loop has completed,
`smallest` contains the minimum value in the list.

Again as in counting and summing, the built-in functions
`max()` and `min()` make writing these exact loops
unnecessary.

The following is a simple version of the Python built-in
`min()` function:

~~~~ {.python}
def min(values):
    smallest = None
    for value in values:
        if smallest is None or value < smallest:
            smallest = value
    return smallest
~~~~

In the function version of the smallest code, we removed all of the
`print` statements so as to be equivalent to the
`min` function which is already built in to Python.

Debugging
---------

As you start writing bigger programs, you might find yourself spending
more time debugging. More code means more chances to make an error and
more places for bugs to hide.

\index{debugging!by bisection}
\index{bisection, debugging by}

One way to cut your debugging time is "debugging by bisection." For
example, if there are 100 lines in your program and you check them one
at a time, it would take 100 steps.

Instead, try to break the problem in half. Look at the middle of the
program, or near it, for an intermediate value you can check. Add a
`print` statement (or something else that has a verifiable
effect) and run the program.

If the mid-point check is incorrect, the problem must be in the first
half of the program. If it is correct, the problem is in the second
half.

Every time you perform a check like this, you halve the number of lines
you have to search. After six steps (which is much less than 100), you
would be down to one or two lines of code, at least in theory.

In practice it is not always clear what the "middle of the program" is
and not always possible to check it. It doesn't make sense to count
lines and find the exact midpoint. Instead, think about places in the
program where there might be errors and places where it is easy to put a
check. Then choose a spot where you think the chances are about the same
that the bug is before or after the check.

Glossary
--------

accumulator
:   A variable used in a loop to add up or accumulate a result.
\index{accumulator}

counter
:   A variable used in a loop to count the number of times something
    happened. We initialize a counter to zero and then increment the
    counter each time we want to "count" something.
\index{counter}

decrement
:   An update that decreases the value of a variable.
\index{decrement}

initialize
:   An assignment that gives an initial value to a variable that will be
    updated.

increment
:   An update that increases the value of a variable (often by one).
\index{increment}

infinite loop
:   A loop in which the terminating condition is never satisfied or for
    which there is no terminating condition.
\index{infinite loop}

iteration
:   Repeated execution of a set of statements using either a function
    that calls itself or a loop.
\index{iteration}

Exercises
---------

Exercise 1: Write a program which repeatedly reads numbers until the
user enters "done". Once "done" is entered, print out the total, count,
and average of the numbers. If the user enters anything other than a
number, detect their mistake using `try` and
`except` and print an error message and skip to the next
number.

~~~~
Enter a number: 4
Enter a number: 5
Enter a number: bad data
Invalid input
Enter a number: 7
Enter a number: done
16 3 5.333333333333333
~~~~

Exercise 2: Write another program that prompts for a list of numbers as
above and at the end prints out both the maximum and minimum of the
numbers instead of the average.

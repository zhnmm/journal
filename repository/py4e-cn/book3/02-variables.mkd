变量、表达式、语句
======================================

值与类型
----------------

\index{value}
\index{type}
\index{string}

**值** 是程序要处理的一个基本要素，如一个字母或一个数字。目前为止，我们接触到的值有`1`、`2`和“Hello, World!”。

这些值属于不同的**类型**：2是整数，“Hello, World!”是**字符串**（因包含一“串”字母而得名）。因为字符串都在引号当中，你（以及解释器）可以根据引号来识别它们。

\index{quotation mark}

`print`语句也可以打印整数。输入python命令启动解释器。

~~~~ {.python}
python
>>> print(4)
4
~~~~

如果不确定一个值属于哪种类型，可以用解释器来确定。

~~~~ {.python .trinket height="160"}
>>> type('Hello, World!')
<class 'str'>
>>> type(17)
<class 'int'>
~~~~

显而易见，字符串属于`str`类型，整数属于`int`类型。需要注意的是，带小数点的数字使用**浮点**（floating-point）格式表示，称为`float`类型。

\index{type}
\index{string type}
\index{class!str}
\index{int type}
\index{class!int}
\index{float type}
\index{class!float}

~~~~ {.python .trinket height="120"}
>>> type(3.2)
<class 'float'>
~~~~

那么，像'17'和'3.2'这种属于哪种类型呢？看起来像数字，但它们和字符串一样被放在单引号里面。

\index{quotation mark}

~~~~ {.python .trinket  height="160"}
>>> type('17')
<class 'str'>
>>> type('3.2')
<class 'str'>
~~~~

它们是字符串。

输入较大的数字时，你可能会在每三个数字之间加一个逗号，例如，`1,000,000`。在Python中这不是一个合法的整数，但这句话是合法的：

~~~~ {.python .trinket height="120"}
>>> print(1,000,000)
1 0 0
~~~~

不过，这根本不是我们想要的！Python把`1,000,000`解释成了一个逗号分隔的整数序列，它把三部分依次打印出来了，中间用空格分隔。

\index{semantic error}
\index{error!semantic}
\index{error message}

这是我们遇到的第一个语义错误例子：代码成功运行，没有任何错误信息，但是它并没有做“正确的事“。

变量
---------

\index{variable}
\index{assignment statement}
\index{statement!assignment}

编程语言最强大的功能之一体现在对**变量**的操控能力。变量是指向一个值的名称。

**赋值** 语句用来创建新变量并对其赋值：

~~~~ {.python}
>>> message = 'And now for something completely different'
>>> n = 17
>>> pi = 3.1415926535897931
~~~~

这个例子列举了三个赋值语句。第一条语句将字符串赋值给变量`message`；第二条语句将整数`17`赋值给变量`n`，第三条语句将 $\pi$ 的(近似)值赋值给变量`pi`。

你可以使用打印语句来显示一个变量的值：

~~~~ {.python}
>>> print(n)
17
>>> print(pi)
3.141592653589793
~~~~

变量的类型就是它所指向的值的类型。

~~~~ {.python}
>>> type(message)
<class 'str'>
>>> type(n)
<class 'int'>
>>> type(pi)
<class 'float'>
~~~~

变量名与关键字
---------------------------

\index{keyword}

程序员通常会选择有意义的变量名，并且在说明书中写明其用途。

变量名不限长度，可以同时包含字母和数字，但是不能以数字开头。使用大写字母也是合法的，但以小写字母开头会更好（之后你会明白原因）。

下划线（`_`）可以出现在变量名中。它经常用在含有多个词的变量名中，例如，`my_name`和`airspeed_of_unladen_swallow`。变量名可以采用下划线开头，但我们一般会避免这样命名，除非是在编写供他人使用的Python库代码。

\index{underscore character}

如果使用不合法的变量名，你就会遇到一个语法错误：

~~~~ {.python .trinket height="450"}
>>> 76trombones = 'big parade'
SyntaxError: invalid syntax
>>> more@ = 1000000
SyntaxError: invalid syntax
>>> class = 'Advanced Theoretical Zymurgy'
SyntaxError: invalid syntax
~~~~

`76trombones`是不合法的变量名，因为它是以数字开头的。`more@`也是不合法的，因为它包含了一个不合法的字符`@`。不过变量名class错在哪呢？

原因在于，`class`是Python的**关键字**。Python解释器使用关键字来识别程序的结构，因此，关键字不能用作变量名。

\index{keyword}

Python保留了31个关键字：

~~~~
and       del       from      None      True
as        elif      global    nonlocal  try
assert    else      if        not       while
break     except    import    or        with
class     False     in        pass      yield
continue  finally   is        raise
def       for       lambda    return
~~~~

你可以在手边存留一份。如果解释器在一个变量名那里报错，而你又不知道为什么，那么检查一下它是否在这个列表里面。

语句
----------

**语句** 是Python解释器能够执行的代码单元。我们已经见到过两种语句：print和assignment。

\index{statement}
\index{interactive mode}
\index{script mode}

当你在交互模式中输入一条语句，解释器就会执行它并打印出结果（如果有结果的话）。

一个脚本通常包含一连串的语句。如果超过一句的话，结果会随着程序的执行，一句一句地产生。

如，以下脚本：

~~~~ {.python}
print(1)
x = 2
print(x)
~~~~

产生下列结果：

~~~~
1
2
~~~~

其中，赋值语句没有输出结果。

运算符和运算对象
----------------------

\index{operator, arithmetic}
\index{arithmetic operator}
\index{operand}
\index{expression}

**运算符** 是表示运算的特殊符号，例如，加法与乘法。运算符操作的值称为运算对象(或运算数，译者注)。

`+`、`-`、`*`、`/`和`**`五个运算符分别代表加、减、乘、除和次方的运算，请看如下示例：

~~~~ {.python}
20+32   hour-1   hour*60+minute   minute/60   5**2   (5+9)*(15-7)
~~~~

对于除法运算符而言，Python 2.x 版本和 Python 3.x 版本有一点区别。在 Python 3.x 中，除法的结果是一个浮点数：

~~~~ {.python .trinket height="160"}
>>> minute = 59
>>> minute/60
0.9833333333333333
~~~~

在 Python 2.0 中，两个整数相除，会得到一个被截断的整数（0.59，会被截断成0，译者注）：

~~~~ {.python}
>>> minute = 59
>>> minute/60
0
~~~~

要想在 Python 3.0 中得到和上面一样的结果，要使用地板除法（ // 整数 ）。

~~~~ {.python .trinket  height="160"}
>>> minute = 59
>>> minute//60
0
~~~~

在 Python 3.0 中，整数相除的结果会像你所期望的那样，和你使用计算器得到的结果一样。

\index{Python 3.0}
\index{Python 2.0}
\index{floating-point division}
\index{division!floating-point}

表达式
-----------

**表达式** 是值、变量和运算符的组合。值本身可以是一个表达式，变量亦如此。所以下面都是合法的表达式（假设变量x已被赋值）：

\index{expression}
\index{evaluate}

~~~~ {.python}
17
x
x + 17
~~~~

如果在交互模式中输入一个表达式，解释器就会**运算**它并把结果打印出来:

~~~~ {.python}
>>> 1 + 1
2
~~~~

然而，在一个程序中，表达式本身并不能做任何事情！这是初学者容易混淆的一点。

习题 1: 在Python解释器中输入下面的语句并查看结果：

~~~~ {.python}
5
x = 5
x + 1
~~~~

运算顺序
-------------------

\index{order of operations}
\index{rules of precedence}
\index{PEMDAS}

当一个表达式中出现多个运算符时，运算顺序由优先级规则来确定。对于数学运算符来说，Python遵照数学运算习惯，即“括号、次方、乘除、加减”。

\index{parentheses!overriding precedence}

-   **括号** 拥有最高运算优先级，可以强制表达式按特定顺序运算。括号内的表达式最先进行运算，例如，`2 * (3-1)` 等于4，`(1+1)**(5-2)` 等于8。有时候，使用括号即便没有改变运算结果，但阅读起来会更加方便，例如，(minute * 100) / 60。

-   **幂运算**（次方、乘方）的优先级仅次于括号，例如，`2**1+1` 等于3，而不是4，`3*1**3`等于3，而不是27。

-   **乘法** 和 **除法** 具有相同的优先级，**加法** 和 **减法** 也具有相同的优先级，且乘除高于加减。所以，`2*3 -1`等于5，而不是 4，`6+4/2`等于8.0，而不是5。

-   相同优先级的运算符按从左到右的顺序依次运算。所以，`5-3-1`等于1，而不是3。先计算`5-3`得到2，然后再减1。

当不能确定运算顺序时，通常使用括号来确保我们想要的运算顺序。

模运算
----------------

\index{modulus operator}
\index{operator!modulus}

**模** 的运算对象是整数，得到的是第一个整数除以第二个整数的余数。在Python中，模运算符用百分号（`%`）表示，语法与其他运算符一样：

~~~~ {.python .trinket height="240"}
>>> quotient = 7 // 3
>>> print(quotient)
2
>>> remainder = 7 % 3
>>> print(remainder)
1
~~~~

如，7被3所除的商是2，余数是1。

模运算非常实用。举例来说，你可以检验一个数是否能被另一个数整除，如果`x%y`的结果是0，那么`x`能被`y`整除。

\index{divisibility}

另外，模运算也可以提取一个数字最右边的数位。举例来说，`x%10`可以提取`x`最右边的一位数字（以10为基数）。同理，`x%100`可以提取最右边的两位数字。

字符串运算符
-----------------

\index{string!operation}
\index{operator!string}

加号 `+` 也可以操作于字符串，但是这时它不是数学里面加法的含义，而是，它会把字符串首尾**串联**。例如：

\index{串联}

~~~~ {.python}
>>> first = 10
>>> second = 15
>>> print(first+second)
25
>>> first = '100'
>>> second = '150'
>>> print(first + second)
100150
~~~~

这个程序的输出结果是`100150`。

请求用户输入
-------------------------

\index{keyboard input}

有时候我们希望获取用户通过键盘输入的值。Python提供了一个内置函数叫`input`，用来获取键盘输入^[在Python 2.0中，这个函数叫做`raw_input`]。当调用这个函数时，程序会暂停运行，等待用户的输入。当用户按下`回车键`(`Return`或`Enter`)时，程序就会恢复运行，`input`函数会以字符串形式返回用户输入的值。

\index{Python 2.0}

~~~~ {.python}
>>> input = input()
Some silly stuff
>>> print(input)
Some silly stuff
~~~~

在请求用户输入之前，最好打印一条提示语句，告诉用户需要输入些什么。你可以通过在`input`中插入一个字符串来提示用户。

\index{prompt}

~~~~ {.python}
>>> name = input('What is your name?\n')
What is your name?
Chuck
>>> print(name)
Chuck
~~~~

提示语结尾的 `\n` 表示**换行符**，它是一个用于截断当前行，并开始下一行的特殊字符。这样一来，用户输入的位置就在提示语句的下面。

\index{newline}

如果希望用户输入一个整数，你可以尝试用`int()`函数将返回的值转换成**整数**型：

~~~~ {.python}
>>> prompt = 'What...is the airspeed velocity of an unladen swallow?\n'
>>> speed = input(prompt)
What...is the airspeed velocity of an unladen swallow?
17
>>> int(speed)
17
>>> int(speed) + 5
22
~~~~

但是，如果用户输入的不是由数字组成的字符串，那么就会报错：

~~~~ {.python}
>>> speed = input(prompt)
What...is the airspeed velocity of an unladen swallow?
What do you mean, an African or a European swallow?
>>> int(speed)
ValueError: invalid literal for int() with base 10:
~~~~

之后，我们会学习该如何处理这类错误。

\index{ValueError}
\index{exception!ValueError}

注释
--------

\index{comment}

当程序变得越来越长并且越来越复杂时，阅读难度也随之增大。正式的程序代码很密集，经常会遇到看不懂这段代码是做什么的，或者为什么要这样写。

为解决这个问题，在程序代码中加入自然语言说明，来解释这段代码的作用，这会是一个不错的主意。这些说明称为**注释**，它们以`#`号开头：

~~~~ {.python}
# compute the percentage of the hour that has elapsed
percentage = (minute * 100) / 60
~~~~

上面这种情况，注释本身占一行。你也可以把它加到一行代码的末尾：

~~~~ {.python}
percentage = (minute * 100) / 60     # percentage of an hour
~~~~

从`\#`号开始到这一行的最后，解释时都会被忽略掉，它们不会对程序产生任何影响。

对代码不显著的特征进行注释是非常有用的。我们可以合理假设读者能够理解代码在**做什么**，但是更有用的是，解释一下**为什么**。

下面这行注释就是多余的，没什么作用：

~~~~ {.python}
v = 5     # assign 5 to v
~~~~

而下面的这行注释则包含了有用的信息，是单纯地看代码看不出来的：

~~~~ {.python}
v = 5     # velocity in meters/second.
~~~~

清晰易懂的变量名能够减少注释的使用，但是变量名如果太长，就会使复杂的表达式变得更加难懂，所以需要权衡利弊。

助记变量命名法
--------------------------------

\index{mnemonic}

只要遵循变量命名的简单规则，避免使用保留字，你给变量取名字的时候还是有很多种选择的。

编程入门阶段，你在阅读别人的程序和编写自己的程序时，对变量的命名可能会感到困惑。例如，下面三个程序所完成的任务在实质上是一样的，但是阅读和理解起来差别却很大。

~~~~ {.python}
a = 35.0
b = 12.50
c = a * b
print(c)
~~~~

~~~~ {.python}
hours = 35.0
rate = 12.50
pay = hours * rate
print(pay)
~~~~

~~~~ {.python}
x1q3z9ahd = 35.0
x1q3z9afd = 12.50
x1q3p9afd = x1q3z9ahd * x1q3z9afd
print(x1q3p9afd)
~~~~

Python解释器看到这三个程序时，会觉得是**完全一样**的。但是对于人而言，阅读和理解它们却是非常不一样的。读者能够快速看懂的是第二个程序的**目的**，这是因为该程序员选择了能够代表变量取值含义的变量名。

这种变量命名法称为“助记变量命名法”。助记^[对于“助记”的详细介绍，请参见 <http://en.wikipedia.org/wiki/Mnemonic>的意思就是帮助记忆。选择易于记忆的变量名，有助于我们记住当初创建这个变量是为了做什么。

这看起来不错，使用助记变量命名法是一个好主意，但可能也会妨碍初学者解析并理解代码。这是由于初学者可能还没有记全Python的33个保留关键字，如果变量名中包含太多描述性的词语，精心命名的变量看上去会像是Python语言的一部分，对初学者理解上造成干扰。

下面两行简单的Python代码实现了循环。循环将在第5章介绍，这里尝试猜猜这两行代码的含义：

~~~~ {.python}
for word in words:
    print(word)
~~~~

这里发生了什么呢？上面哪些（for, word, in, 等）是保留字，哪些只是变量名呢？Python能理解单词的基本含义吗？初学者很难分辨出代码中哪些部分**必须**照抄示例中的，而哪些部分是可以由程序员自主选择的。

下面的代码和上面的在实质上是一样的：

~~~~ {.python}
for slice in pizza:
    print(slice)
~~~~

初学者可以较容易的从这段代码中判断哪些是Python定义的保留字，哪些是程序员选择的变量名。Python显然不能理解 pizza（披萨） 和 slices（块） 的含义，更不用说披萨可以被切成很多块这个事实了。

但是，如果我们的程序实际上是要读取数据并在数据中查找单词的话，`pizza` 和 `slice` 就是非常不易记的变量名了。选择它们作为变量名就会偏离程序的本意。

用不了多久，你就会熟悉最常用的保留字，并会在程序中注意到它们：

` word *in* words*:*\
`    `*print* word `

这段代码中，由Python定义的部分被加粗了（`for`, `in`, `print`, 和 `:`），程序员选择的变量名（`word` 和 `words`）则没有被加粗。很多文本编辑器能感知到Python的语法，并且会用不同的颜色来标记保留字，以让你能够更好的区分变量名与保留字。熟悉一段时间后，你就会很快地区分哪些是变量名，哪些保留字了。

调试
---------

\index{debugging}

目前，你最容易犯的语法错误应该是使用了一个不合法的变量名，比如 `class` 和 `yield`，它们是保留字，又或者 `odd~job` 和 `US$`，它们含有不合法的字符。

\index{语法错误}
\index{错误!语法}

如果你在变量名中放一个空格，Python会认为它是没有运算符的两个运算对象：

~~~~ {.python}
>>> bad name = 5
SyntaxError: invalid syntax
~~~~

~~~~ {.python}
>>> month = 09
  File "<stdin>", line 1
    month = 09
             ^
SyntaxError: invalid token
~~~~

对语法错误而言，错误信息并不能提供多少帮助。最常见的信息是 `SyntaxError: invalid syntax` 和 `SyntaxError: invalid token`，而这两条都没什么信息量。

\index{错误信息}
\index{定义前使用}
\index{例外}
\index{运行错误}
\index{错误!运行}

最常遇到的运行错误是“use before def;（定义前就使用）”，也就是，你在尝试使用一个还没有被赋值的变量。变量名拼写不正确就会导致这个错误：

~~~~ {.python}
>>> principal = 327.68
>>> interest = principle * rate
NameError: name 'principle' is not defined
~~~~

变量名区分大小写，所以，`LaTeX` 和 `latex` 是不一样的。

\index{区分大小写, 变量名}
\index{语义错误}
\index{错误!语义}

目前，最容易犯的语义错误在运算顺序上。比如，要运算 $1/2\pi$，你可能会写成这样：

~~~~ {.python}
>>> 1.0 / 2.0 * pi
~~~~

而这样的话，就是先进行除法运算，得到的是 $\pi / 2$，和你的目的不一样！但是Python并不明白你想要表达的是什么，所以在这种情况下，它并不会报错，但是你得到的答案不是你想要的。

\index{运算顺序}

术语表
--------

赋值
:   给变量赋予一个值的语句。
\index{赋值}

串联
:   将两个运算对象首位相连。
\index{串联}

注释
:   程序里面包含的信息，旨在帮助其他程序员（或任何查看源码的人）理解程序，而不会对程序的执行产生任何影响。
\index{注释}

求值
:   对表达式进行运算，得到单个值。

表达式
:   变量、运算符和值的组合，表示单个结果值。
\index{表达式}

浮点数
:   代表有小数部分的数值类型。
\index{浮点数}

整数
:   代表整数类型
\index{整数}

关键字
:   Python解释器用来解析程序的保留字。变量名不能使用保留字，如 `if`, `def`, 和 `while` 等。
\index{关键字}

助记法
:   一种辅助记忆的方法。我们通常使用易记的变量名来帮助我们记住变量存储的内容。
\index{助记法}

模运算
:   一种运算符，用百分号（`%`）表示，求两个整数相除的余数。
\index{模运算}
\index{运算符!模}

运算对象
:   运算符操作的值。
\index{运算对象}

运算符
:   代表着简单运算的一类特殊符号，如加法、乘法和字符串串联。
\index{运算符}

运算优先级
:   一组运算规则，用来规定在有多个运算符和运算对象的表达式中的求值顺序。
\index{运算优先级}
\index{优先级}

语句
:   表示一个命令的一段代码。目前为止，我们见到的语句有赋值语句和打印语句。
\index{语句}

字符串
:   由字符序列组成的一种数据类型。
\index{字符串}

类型
:   表示一类值。目前，我们已经见到的类型有整数（`int`），浮点数（`float`），和字符串（`str`）。
\index{类型}

值
:   数据的一种基本单元。如一个数字或一个字符串，可以被程序操作。
\index{值}

变量
:   一个值的引用名称。
\index{变量}

习题
---------

习题 2: 使用 `input` 编写一个程序，提示用户输入姓名，然后打印欢迎语。

~~~~
Enter your name: Chuck
Hello Chuck
~~~~

习题 3: 编写一个程序，提示用户输入工时和时薪，然后计算出总工资。

~~~~
Enter Hours: 35
Enter Rate: 2.75
Pay: 96.25
~~~~

我们暂时不用担心我们计算的结果是否能正好精确到小数点后两位。如果你非常想的话，可以试一试Python内置的 `round` 函数，它可以把结果约到两位数。

Exercise 4: 假设我们执行了下面的赋值语句：

~~~~
width = 17
height = 12.0
~~~~

对于下面每一个表达式，写出它的结果，及其结果类型。

1.  `width//2`

2.  `width/2.0`

3.  `height/3`

4.  `1 + 2 \* 5`

使用Python解释器检查你的结果。

Exercise 5: 写一个程序，提示用户输入摄氏温度，然后将其转化成华氏温度，并且把结果打印出来。



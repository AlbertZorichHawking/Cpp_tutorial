#### For循环

很多情况下都需要程序执行重复的任务，如将数组中的元素累加起来或将打印20次语句。

~~~c++
# include <iostream>
using namespace std; 
int main ()
{
    int i;//create a counter 
    //initialize; test ; update 
    for (i= 0; i < 5; i++)
        cout << "C++ knows loops. \n"; 
    cout << "C++ knows when to stop. \n"; 
    return 0;
}
~~~

程序输出

~~~c++
C++ knows loops.
C++ knows 1oops.
C++ knows loops.
C++ knows 1oops.
C++ knows loops.
C++ knows when to stop.
~~~

该循环首先将整数变量i设置为0：

```c++
i = 0
```

这是循环的初始化（loop initialization）部分。然后，循环测试 （loop test）部分检查i是否小于5：

```c++
i < 5
```

如果确实小于5，则程序将执行接下来的语句—循环体（loop body）：

~~~c++
cout << "C++ knows loops. \n"; 
~~~

 然后，程序使用循环更新（loop update）部分将i加1：

```c++
i++
```

接下来，循环开始了新的周期，将新的i值与5进行比较。由于新值 （1）也小于5，因此循环打印另一行，然后再次将i加1，从而结束这一 周期。这样又进入了新的一轮测试、执行语句和更新i的值。这一过程 将一直进行下去，直到循环将i更新为5为止。这样，接下来的测试失 败，程序将接着执行循环后的语句。

##### For循环的组成部分

for循环的组成部分完成下面这些步骤。

1. 设置初始值。 

2. 执行测试，看看循环是否应当继续进行。 

3. 执行循环操作。

4. 更新用于测试的值。

C++循环设计中包括了这些要素，很容易识别。初始化、测试和更新操作构成了控制部分，这些操作由括号括起。其中每部分都是一个表达式，彼此由分号隔开。控制部分后面的语句叫作循环体，只要测试表达式为true，它便被执行：

~~~c++
for (initialization; test-expression; update-expression)
    body
~~~

C++语法将整个for看作一条语句—虽然循环体可以包含一条或多条 语句。(包含多条语句时，需要使用复合语句或代码块)

循环只执行一次初始化。通常，程序使用该表达式将变量设置为起始值，然后用该变量计算循环周期。

test-expression（测试表达式）决定循环体是否被执行。通常，这个 表达式是关系表达式，即对两个值进行比较。实际 上，C++并没有将test-expression的值限制为只能为真或假。可以使用任 意表达式，C++将把结果强制转换为bool类型。因此，值为0的表达式将 被转换为bool值false，导致循环结束。如果表达式的值为非零，则被强 制转换为bool值true，循环将继续进行。

~~~c++
#include <iostream>
using namespace std;
int main ()
{
    cout << "Enter the starting countdown value:";
    int limit; 
    cin >>limit;
    int i; 
    for (i = limit; i; i--)// quits when i is 0
        cout << "i = "<< i <<"n"
    cout << "Done now that i = " << i << "\n";
    return 0;
}
~~~

程序结果：

~~~c++
Enter the starting countdown value: 4
i = 4
i = 3
i = 2
i = 1
Done now that i =  
~~~

for循环是入口条件（entry-condition）循环。这意味着在每轮循环 之前，都将计算测试表达式的值，当测试表达式为false时，将不会执行 循环体。for循环是入口条件（entry-condition）循环。这意味着在每轮循环 之前，都将计算测试表达式的值，当测试表达式为false时，将不会执行循环体。

##### 修改步长

到现在为止，循环示例每一轮循环都将循环计数加1或减1。可以通 过修改更新表达式来修改步长。

~~~c++
#include <iostream>
int main ()
{
    using std:: cout;// a using declaration 
    using std::cin; 
    using std: :endl; 
    cout <<"Enter an integer: ";
    int by; 
    cin >>by; 
    cout << "Counting by"<<by<<"s:\n";
    for (int i = 0; i < 100; i= i + by)
         cout << i << endl; 
    return 0;
}
~~~

运行结果

~~~
Enter an integer:17
Counting by 17S:
0
17
34
51
68
85
~~~

当i的值到达102时，循环终止。这里的重点是，更新表达式可以是 任何有效的表达式。例如，如果要求每轮递增以i的平方加10，则可以 使用表达式i = i * i + 10。 需要指出的另一点是，检测不等通常比检测相等好。例如，在这里 使用条件i == 100不可行，因为i的取值不会为100。

##### 复合语句（语句块）

对于
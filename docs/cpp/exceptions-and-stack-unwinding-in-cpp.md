---
title: C++ 中的异常和堆栈展开
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: 11657206e86dbc81eb62c1e11b49fd87777f11d8
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246570"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ 中的异常和堆栈展开

在 C++ 异常机制中，控制从 throw 语句移至可处理引发类型的第一个 catch 语句。 当到达 catch 语句时，将在称为*堆栈展开*的进程中销毁 throw 和 catch 语句之间范围内的所有自动变量。 在堆栈展开中，执行将继续，如下所示：

1. Control 通过正常顺序执行到达**try**语句。 执行**try**块中的受保护部分。

1. 如果在执行受保护部分的过程中未引发异常，则不会执行位于**try**块后面的**catch**子句。 在关联的**try**块后面的最后一个**catch**子句之后的语句中继续执行。

1. 如果在受保护节的执行过程中或在受保护的部分直接或间接调用的任何例程中引发异常，则将从由**throw**操作数创建的对象创建异常对象。 （这意味着可能会涉及复制构造函数。）此时，编译器会在更高的执行上下文中查找**catch**子句，该子句可以处理引发的类型的异常，或用于可处理任何类型的异常的**catch**处理程序。 将按其在**try**块后的外观顺序检查**捕获**处理程序。 如果找不到合适的处理程序，则检查下一个动态封闭**try**块。 此过程将继续，直到检查最外面的封闭**try**块。

1. 如果仍未找到匹配的处理程序，或者在展开过程中但在处理程序获得控制前发生异常，则调用预定义的运行时函数 `terminate`。 如果在引发异常后但在展开开始前发生异常，则调用 `terminate`。

1. 如果找到匹配的**catch**处理程序，并且它通过值进行捕获，则通过复制 exception 对象初始化其形参。 如果它通过引用进行捕获，则初始化参数以引用异常对象。 在初始化形参后，堆栈的展开过程将开始。 这涉及到在与**catch**处理程序关联的**try**块开始与异常的引发站点之间完全构造但尚未销毁的所有自动对象的析构。 析构按照与构造相反的顺序发生。 执行**catch**处理程序，程序在最后一个处理程序之后恢复执行，即，在不是**catch**处理程序的第一个语句或构造处继续执行。 Control 只能通过引发的异常输入**catch**处理程序，从不通过**goto**语句或**switch**语句中的**case**标签来输入。

## <a name="stack-unwinding-example"></a>堆栈展开示例

以下示例演示引发异常时如何展开堆栈。 线程执行将从 `C` 中的 throw 语句跳转到 `main` 中的 catch 语句，并在此过程中展开每个函数。 请注意创建 `Dummy` 对象的顺序，并且会在它们超出范围时将其销毁。 还请注意，除了包含 catch 语句的 `main` 之外，其他函数均未完成。 函数 `A` 绝不会从其对 `B()` 的调用返回，并且 `B` 绝不会从其对 `C()` 的调用返回。 如果取消注释 `Dummy` 指针和相应的 delete 语句的定义并运行程序，请注意绝不会删除该指针。 这说明了当函数不提供异常保证时会发生的情况。 有关详细信息，请参阅“如何：针对异常进行设计”。 如果注释掉 catch 语句，则可以观察当程序因未经处理的异常而终止时将发生的情况。

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```

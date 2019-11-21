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

在 C++ 异常机制中，控制从 throw 语句移至可处理引发类型的第一个 catch 语句。 When the catch statement is reached, all of the automatic variables that are in scope between the throw and catch statements are destroyed in a process that is known as *stack unwinding*. 在堆栈展开中，执行将继续，如下所示：

1. Control reaches the **try** statement by normal sequential execution. The guarded section in the **try** block is executed.

1. If no exception is thrown during execution of the guarded section, the **catch** clauses that follow the **try** block are not executed. Execution continues at the statement after the last **catch** clause that follows the associated **try** block.

1. If an exception is thrown during execution of the guarded section or in any routine that the guarded section calls either directly or indirectly, an exception object is created from the object that is created by the **throw** operand. (This implies that a copy constructor may be involved.) At this point, the compiler looks for a **catch** clause in a higher execution context that can handle an exception of the type that is thrown, or for a **catch** handler that can handle any type of exception. The **catch** handlers are examined in order of their appearance after the **try** block. If no appropriate handler is found, the next dynamically enclosing **try** block is examined. This process continues until the outermost enclosing **try** block is examined.

1. 如果仍未找到匹配的处理程序，或者在展开过程中但在处理程序获得控制前发生异常，则调用预定义的运行时函数 `terminate`。 如果在引发异常后但在展开开始前发生异常，则调用 `terminate`。

1. If a matching **catch** handler is found, and it catches by value, its formal parameter is initialized by copying the exception object. 如果它通过引用进行捕获，则初始化参数以引用异常对象。 在初始化形参后，堆栈的展开过程将开始。 This involves the destruction of all automatic objects that were fully constructed—but not yet destructed—between the beginning of the **try** block that is associated with the **catch** handler and the throw site of the exception. 析构按照与构造相反的顺序发生。 The **catch** handler is executed and the program resumes execution after the last handler—that is, at the first statement or construct that is not a **catch** handler. Control can only enter a **catch** handler through a thrown exception, never through a **goto** statement or a **case** label in a **switch** statement.

## <a name="stack-unwinding-example"></a>Stack unwinding example

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

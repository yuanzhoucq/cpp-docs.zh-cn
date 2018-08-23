---
title: 异常和堆栈展开中 C++ |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cefb6ba2fe076714b420024ec09464fd928b63d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406381"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>C++ 中的异常和堆栈展开
在 C++ 异常机制中，控制从 throw 语句移至可处理引发类型的第一个 catch 语句。 Catch 语句到达时，throw 之间的范围内和 catch 语句的自动变量的所有名为的进程中销毁*堆栈展开*。 在堆栈展开中，执行将继续，如下所示：  
  
1.  控件到达**尝试**通过正常顺序执行的语句。 在受保护的节**尝试**执行块。  
  
2.  如果在受保护节执行过程中不引发任何异常**捕获**子句，其遵循**尝试**块不会执行。 继续执行后的最后一个语句**捕获**子句后面关联**尝试**块。  
  
3.  如果在受保护节的或受保护的节调用的直接或间接的任何例程中的执行期间引发异常，从创建的对象创建的异常对象**引发**操作数。 （这意味着，可能会涉及复制构造函数。）此时，编译器会寻找**捕获**可以处理异常的类型的引发，或更高版本执行上下文中的子句**捕获**可以处理任何类型的异常处理程序。 **捕获**处理程序检查后面的显示顺序**尝试**块。 如果找到任何适当的处理程序，下一个动态封闭**尝试**检查块。 此过程将继续，直到最外面的封闭**尝试**检查块。  
  
4.  如果仍未找到匹配的处理程序，或者在展开过程中但在处理程序获得控制前发生异常，则调用预定义的运行时函数 `terminate`。 如果在引发异常后但在展开开始前发生异常，则调用 `terminate`。  
  
5.  如果匹配**捕获**找到处理程序，并且它通过值捕获，通过复制异常对象初始化其形参。 如果它通过引用进行捕获，则初始化参数以引用异常对象。 在初始化形参后，堆栈的展开过程将开始。 这涉及到完全构造的所有自动对象的析构 — 但尚未 — 开始之间经历的**尝试**与关联的块**捕获**处理程序和引发异常的站点。 析构按照与构造相反的顺序发生。 **捕获**执行处理程序，程序继续执行最后一个处理程序后的，即，在第一个语句或构造，它不是**捕获**处理程序。 只能输入控件**捕获**通过引发的异常处理程序永远不会通过**goto**语句或**用例**中的标签**切换**语句。  
  
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
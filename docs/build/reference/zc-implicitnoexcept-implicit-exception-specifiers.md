---
title: "/Zc:implicitNoexcept（隐式异常说明符） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:implicitNoexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc:implicitNoexcept"
  - "Zc:implicitNoexcept"
  - "-Zc:implicitNoexcept"
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /Zc:implicitNoexcept（隐式异常说明符）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当指定了 **\/Zc:implicitNoexcept** 选项时，编译器将向编译器定义的特殊成员函数以及用户定义的析构函数和释放函数添加隐式 [noexcept](../../cpp/noexcept-cpp.md) 异常说明符。  默认启用了 **\/Zc:implicitNoexcept** 以符合 ISO C\+\+ 11 标准。  关闭此选项将对用户定义的析构函数和释放函数以及编译器定义的特殊成员函数禁用隐式 `noexcept`。  
  
## 语法  
  
```vb  
/Zc:implicitNoexcept[-]  
```  
  
#### 参数  
  
## 备注  
 默认情况下，如果指定了 **\/Zc:implicitNoexcept**，则编译器遵循 ISO C\+\+ 11 标准的第 15.4 节，将 `noexcept` 异常说明符隐式添加到每个隐式声明或显式默认的特殊成员函数（默认构造函数、复制构造函数、移动构造函数、析构函数、复制赋值运算符或移动赋值运算符）和用户定义的每个析构函数或释放函数。  用户定义的释放函数具有隐式 `noexcept(true)` 异常说明符。  对于用户定义的析构函数，隐式异常说明符为 `noexcept(true)`，除非包含的成员类或基类具有非 `noexcept(true)` 的析构函数。  对于编译器生成的特殊成员函数，如果此函数直接调用的任何函数实际上是 `noexcept(false)`，则隐式异常说明符为 `noexcept(false)`。  否则，隐式异常说明符为 `noexcept(true)`。  
  
 编译器不会为通过使用显式 `noexcept` 或 `throw` 说明符或 `__declspec(nothrow)` 属性声明的函数生成隐式异常说明符。  
  
 如果通过指定 **\/Zc:implicitNoexcept\-** 禁用了该选项，则编译器将不会生成任何隐式异常说明符。  此行为与 Visual Studio 2013 相同，其中不具有异常说明符的析构函数和释放函数可具有相同的 `throw` 语句。  默认情况下，指定了 **\/Zc:implicitNoexcept** 时，如果在具有隐式 `noexcept(true)` 说明符的函数中在运行时遇到 `throw` 语句，会导致立即调用 `std::terminate`，且不保证异常处理程序的正常展开行为。  为了帮助识别这种情况，编译器将生成[编译器警告（等级 1）C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)。  如果 `throw` 是有意的，建议更改函数声明，以使用显式 `noexcept(false)` 说明符而不使用 **\/Zc:implicitNoexcept\-**。  
  
 此示例演示当设置或者禁用了 **\/Zc:implicitNoexcept** 选项时，不具有显式异常说明符的用户定义的析构函数的行为方式。  若要演示设置了该选项时的行为，请使用 `cl /EHsc /W4 implicitNoexcept.cpp` 进行编译。  若要演示禁用了该选项时的行为，请使用 `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` 进行编译。  
  
```  
// implicitNoexcept.cpp  
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp  
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp  
  
#include <iostream>  
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS  
#include <exception>    // for std::set_terminate  
  
void my_terminate()  
{  
    std::cout << "Unexpected throw caused std::terminate" << std::endl;  
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;  
    std::exit(EXIT_FAILURE);  
}  
  
struct A {  
    // Explicit noexcept overrides implicit exception specification  
    ~A() noexcept(false) {  
        throw 1;  
    }  
};  
  
struct B : public A {  
    // Compiler-generated ~B() definition inherits noexcept(false)  
    ~B() = default;  
};  
  
struct C {  
    // By default, the compiler generates an implicit noexcept(true)  
    // specifier for this user-defined destructor. To enable it to  
    // throw an exception, use an explicit noexcept(false) specifier,  
    // or compile by using /Zc:implicitNoexcept-  
    ~C() {    
        throw 1; // C4297, calls std::terminate() at run time  
    }  
};  
  
struct D : public C {  
    // This destructor gets the implicit specifier of its base.  
    ~D() = default;  
};  
  
int main()  
{  
    std::set_terminate(my_terminate);  
  
    try  
    {  
        {  
            B b;   
        }  
    }  
    catch (...)  
    {  
        // exception should reach here in all cases  
        std::cout << "~B Exception caught" << std::endl;  
    }  
    try  
    {  
        {  
            D d;  
        }  
    }  
    catch (...)  
    {  
        // exception should not reach here if /Zc:implicitNoexcept  
        std::cout << "~D Exception caught" << std::endl;  
    }  
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;  
    return EXIT_SUCCESS;  
}  
  
```  
  
 通过使用 **\/Zc:implicitNoexcept** 默认设置进行编译时，该示例生成以下输出：  
  
  **已捕获异常 ~B**  
**意外引发导致 std::terminate**  
**退出返回 EXIT\_FAILURE** 使用 **\/Zc:implicitNoexcept\-** 设置进行编译时，该示例生成以下输出：  
  
  **已捕获异常 ~B**  
**已捕获异常 ~D**  
**退出返回 EXIT\_SUCCESS** 有关 Visual C\+\+ 中的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择“命令行”属性页。  
  
4.  修改“附加选项”属性以包含 **\/Zc:implicitNoexcept** 或 **\/Zc:implicitNoexcept\-**，然后选择“确定”。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)   
 [noexcept](../../cpp/noexcept-cpp.md)   
 [异常规范 \(throw\)](../../cpp/exception-specifications-throw-cpp.md)   
 [terminate](../Topic/terminate%20\(%3Cexception%3E\).md)
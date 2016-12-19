---
title: "结构化异常处理 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 异常处理程序"
  - "C++ 异常处理, 终止处理程序"
  - "结构化异常处理"
  - "终止处理程序, 在 C++ 中处理异常"
  - "try-catch 关键字 [C++], 异常处理程序"
  - "try-catch 关键字 [C++], 终止处理程序"
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 结构化异常处理 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尽管 Windows 和 Visual C\+\+ 支持结构化异常处理 \(SEH\)，我们还是建议你使用 ISO 标准 C\+\+ 异常处理，因为它使代码具有更好的可移植性并更灵活。  然而，在现有代码中或者对于特定类型的程序，你仍可能必须使用 SEH。  
  
## Microsoft 专用  
  
## 语法  
 *try\-except\-statement* ：  
  
 `__try` *compound\-statement*  
  
 `__except` \( `expression` \) *compound\-statement*  
  
## 备注  
 使用 SEH，你可以确保执行意外终止时资源（如内存块和文件）是正确的。  你还可以处理特定问题 — 例如，没有足够的内存 — 方法是使用简洁的结构化的代码，该代码不依赖于 `goto` 语句或返回代码的详尽测试。  
  
 这篇文章中引用的 try\-except 和 try\-finally 语句是 C 语言的 Microsoft 扩展。  它们通过使应用程序可以在事件后获得对程序的控制（否则事件将终止执行）来支持 SEH。  尽管 SEH 使用 C\+\+ 源文件，但它并不是专为 C\+\+ 设计的。  如果通过使用 [\/EH](../build/reference/eh-exception-handling-model.md) 选项 — 以及某些修饰符在 C\+\+ 程序中使用 SEH — 则会调用本地对象的析构函数，但其他执行行为可能不是你所预期的。  （有关图示，请参阅本文后面的示例。） 在大多数情况下，我们建议你不使用 SEH 而使用 Visual C\+\+ 同样支持的 ISO 标准 [C\+\+ 异常处理](../cpp/try-throw-and-catch-statements-cpp.md)。  使用 C\+\+ 异常处理可以确保你的代码更具可移植性，并且你可以处理任何类型的异常。  
  
 如果你有使用 SEH 的 C 模块，你可以将它们与使用 C\+\+ 异常处理的 C\+\+ 模块混合使用。  相关信息请参阅[异常处理差异](../cpp/exception-handling-differences.md)。  
  
 有两种 SEH 机制：  
  
-   [异常处理程序](../cpp/writing-an-exception-handler.md)，它可以响应或消除异常。  
  
-   [终止处理程序](../cpp/writing-a-termination-handler.md)，当异常在代码块中引起终止时会调用它。  
  
 这两种类型的处理程序是不同的，但会通过称为“展开堆栈”的过程紧密关联。 发生异常时，Windows 将查找当前处于活动状态的最新安装的异常处理程序。  该处理程序可以执行以下三个操作之一：  
  
-   无法识别该异常并将控件传递给其他处理程序。  
  
-   识别异常，但将其消除。  
  
-   识别异常，并处理异常。  
  
 识别异常的异常处理程序可能不在异常发生时正在运行的函数中。  在某些情况下，它可能在堆栈上高得多的函数中。  当前正在运行的函数和堆栈帧上的所有其他函数都将终止。  在此过程中，堆栈会“展开”；即终止的函数的本地变量（除非它们是 `static`）将从堆栈清除。  
  
 当它展开堆栈时，操作系统将调用你为每个函数编写的任何终止处理程序。  通过使用终止处理程序，你可以清理资源，否则资源将由于异常终止而保持打开状态。  如果你已输入了关键部分，可以在终止处理程序中退出。  如果程序将要关闭，你可以执行其他维护任务，如关闭和删除临时文件。  
  
 有关详细信息，请参见:  
  
-   [编写异常处理程序](../cpp/writing-an-exception-handler.md)  
  
-   [编写终止处理程序](../cpp/writing-a-termination-handler.md)  
  
-   [将结构化异常处理用于 C\+\+](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## 示例  
 正如前文所述，如果你在 C\+\+ 程序中使用 SEH，并通过使用具有某些修饰符的 **\/EH** 选项对其进行编译，则会调用本地对象的析构函数，例如 **\/EHsc** 和 **\/EHa**。  但是，如果你也正在使用 C\+\+ 异常，则执行过程中的行为可能不是你所预期的。  下列示例演示这些行为差异。  
  
```cpp  
#include <stdio.h>  
#include <Windows.h>  
#include <exception>  
  
class TestClass  
{  
public:  
    ~TestClass()  
    {  
        printf("Destroying TestClass!\r\n");  
    }  
};  
  
__declspec(noinline) void TestCPPEX()  
{  
#ifdef CPPEX  
    printf("Throwing C++ exception\r\n");  
    throw std::exception("");  
#else  
    printf("Triggering SEH exception\r\n");  
    volatile int *pInt = 0x00000000;  
    *pInt = 20;  
#endif  
}  
  
__declspec(noinline) void TestExceptions()  
{  
    TestClass d;  
    TestCPPEX();  
}  
  
int main()  
{  
    __try  
    {  
        TestExceptions();  
    }  
    __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf("Executing SEH __except block\r\n");  
    }  
  
    return 0;  
}  
  
```  
  
 如果你使用 **\/EHsc** 来编译此代码，但未定义本地测试控件 `CPPEX`，则不执行 `TestClass` 析构函数，输出如下所示：  
  
  **触发 SEH 异常**  
**执行 SEH \_\_except 块** 如果你使用 **\/EHsc** 来编译代码，且使用 `/DCPPEX` 定义了 `CPPEX`（以致引发 C\+\+ 异常），则执行 `TestClass` 析构函数，输出如下所示：  
  
  **引发 C\+\+ 异常**  
**销毁 TestClass！  执行 SEH \_\_except 块**  如果你使用 **\/EHa** 来编译代码，则无论是通过使用 `std::throw` 还是通过使用 SEH 来触发异常，都会执行 `TestClass` 析构函数（已定义 `CPPEX` 或未定义）。  输出如下所示：  
  
  **引发 C\+\+ 异常**  
**销毁 TestClass！  执行 SEH \_\_except 块**  有关详细信息，请参阅 [\/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md)。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [\<exception\>](../standard-library/exception.md)   
 [错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [结构化异常处理 \(Windows\)](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)
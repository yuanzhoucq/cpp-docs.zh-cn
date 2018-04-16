---
title: 结构化异常处理 （C/c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37d5a89ebf95d8852664dcd50e44e82009ebd95e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)
尽管 Windows 和 Visual C++ 支持结构化异常处理 (SEH)，我们还是建议你使用 ISO 标准 C++ 异常处理，因为它使代码具有更好的可移植性并更灵活。 然而，在现有代码中或者对于特定类型的程序，你仍可能必须使用 SEH。  
  
## <a name="microsoft-specific"></a>Microsoft 专用  
  
## <a name="grammar"></a>语法  
 *try 除语句*:  
  
 `__try`*复合语句*  
  
 `__except`( `expression` )*复合语句*  
  
## <a name="remarks"></a>备注  
 使用 SEH，你可以确保执行意外终止时资源（如内存块和文件）是正确的。 你还可以处理特定问题 — 例如，没有足够的内存 — 方法是使用简洁的结构化的代码，该代码不依赖于 `goto` 语句或返回代码的详尽测试。  
  
 这篇文章中引用的 try-except 和 try-finally 语句是 C 语言的 Microsoft 扩展。 它们通过使应用程序可以在事件后获得对程序的控制（否则事件将终止执行）来支持 SEH。 尽管 SEH 使用 C++ 源文件，但它并不是专为 C++ 设计的。 如果在通过使用 c + + 程序中使用 SEH [/EH](../build/reference/eh-exception-handling-model.md)选项 — 以及某些修饰符-会调用本地对象的析构函数，但其他执行行为可能不是你的预期。 （有关图示，请参阅本文后面的示例。）在大多数情况下，而不是 SEH 我们建议你使用 ISO 标准[c + + 异常处理](../cpp/try-throw-and-catch-statements-cpp.md)，Visual c + + 还支持。 使用 C++ 异常处理可以确保你的代码更具可移植性，并且你可以处理任何类型的异常。  
  
 如果你有使用 SEH 的 C 模块，你可以将它们与使用 C++ 异常处理的 C++ 模块混合使用。 有关信息，请参阅[异常处理差异](../cpp/exception-handling-differences.md)。  
  
 有两种 SEH 机制：  
  
-   [异常处理程序](../cpp/writing-an-exception-handler.md)，它们可以响应或消除异常。  
  
-   [终止处理程序](../cpp/writing-a-termination-handler.md)，当异常在代码块中引起终止时会调用它。  
  
 这两种类型的处理程序是不同的，但会通过称为“展开堆栈”的过程紧密关联。 发生异常时，Windows 将查找当前处于活动状态的最新安装的异常处理程序。 该处理程序可以执行以下三个操作之一：  
  
-   无法识别该异常并将控件传递给其他处理程序。  
  
-   识别异常，但将其消除。  
  
-   识别异常，并处理异常。  
  
 识别异常的异常处理程序可能不在异常发生时正在运行的函数中。 在某些情况下，它可能在堆栈上高得多的函数中。 当前正在运行的函数和堆栈帧上的所有其他函数都将终止。 在此过程中，堆栈会“展开”；即终止的函数的本地变量（除非它们是 `static`）将从堆栈清除。  
  
 当它展开堆栈时，操作系统将调用你为每个函数编写的任何终止处理程序。 通过使用终止处理程序，你可以清理资源，否则资源将由于异常终止而保持打开状态。 如果你已输入了关键部分，可以在终止处理程序中退出。 如果程序将要关闭，你可以执行其他维护任务，如关闭和删除临时文件。  
  
 有关详细信息，请参见:  
  
-   [编写异常处理程序](../cpp/writing-an-exception-handler.md)  
  
-   [编写终止处理程序](../cpp/writing-a-termination-handler.md)  
  
-   [将结构化异常处理用于 C++](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>示例  
 如上文所述，析构函数会调用本地对象，如果你在 c + + 程序中使用 SEH，并通过对其进行编译的**/EH**具有某些修饰符的选项 — 例如， **/EHsc**和**/EHa**. 但是，如果你也正在使用 C++ 异常，则执行过程中的行为可能不是你所预期的。 下面的示例演示这些行为差异。  
  
```cpp  
#include <stdio.h>  
#include <Windows.h>  
#include <exception>  
  
class TestClass  
{  
public:  
    ~TestClass()  
    {  
        printf("Destroying TestClass!\r\n");  
    }  
};  
  
__declspec(noinline) void TestCPPEX()  
{  
#ifdef CPPEX  
    printf("Throwing C++ exception\r\n");  
    throw std::exception("");  
#else  
    printf("Triggering SEH exception\r\n");  
    volatile int *pInt = 0x00000000;  
    *pInt = 20;  
#endif  
}  
  
__declspec(noinline) void TestExceptions()  
{  
    TestClass d;  
    TestCPPEX();  
}  
  
int main()  
{  
    __try  
    {  
        TestExceptions();  
    }  
    __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf("Executing SEH __except block\r\n");  
    }  
  
    return 0;  
}  
  
```  
  
 如果你使用**/EHsc**来编译此代码，但本地测试控件`CPPEX`是未定义，则不执行的`TestClass`析构函数，输出如下所示：  
  
```Output  
Triggering SEH exception  
Executing SEH __except block  
```  
  
 如果你使用**/EHsc**来编译代码和`CPPEX`使用定义`/DCPPEX`（以致引发 c + + 异常），则`TestClass`析构函数执行并输出如下所示：  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 如果你使用**/EHa**来编译代码，`TestClass`析构函数而不考虑是否使用引发异常时执行`std::throw`或通过使用 SEH 来触发异常 (`CPPEX`或未定义)。 输出如下所示：  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 有关详细信息，请参阅 [/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [\<exception>](../standard-library/exception.md)   
 [错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [结构化的异常处理 (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)
---
title: Structured Exception Handling (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: b77a218340399578e3c9428100476787e2e60b25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534558"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

结构化的异常处理 (SEH) 是 Microsoft 扩展到 C 来适当地处理某些异常代码的情况下，例如硬件故障。 尽管 Windows 和 Visual c + + 支持 SEH，但我们建议你使用 ISO 标准 c + + 异常处理，因为它使代码更可移植并更灵活。 不过，若要维护现有代码或为特定类型的程序，您仍可能必须使用 SEH。

**Microsoft 专用：**

## <a name="grammar"></a>语法

*try 除语句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *复合语句* **__except** **(** *表达式* **)** *复合语句*

*try-最后-语句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *复合语句* **__finally** *复合语句*

## <a name="remarks"></a>备注

使用 SEH，可以确保正确释放内存块和文件等资源如果执行意外终止。 你还可以处理特定问题 — 例如，没有足够的内存-使用简洁的结构化的代码，不依赖于**goto**语句或返回代码的详尽测试。

这篇文章中引用的 try-except 和 try-finally 语句是 C 语言的 Microsoft 扩展。 它们通过使应用程序可以在事件后获得对程序的控制（否则事件将终止执行）来支持 SEH。 尽管 SEH 使用 C++ 源文件，但它并不是专为 C++ 设计的。 如果在使用编译的 c + + 程序中使用 SEH [/EHa 或 /EHsc](../build/reference/eh-exception-handling-model.md)选项，析构函数会调用本地对象，但其他执行行为可能不是你期望的内容。 有关说明，请参阅本文后面的示例。 在大多数情况下，而不是 SEH 我们建议你使用 ISO 标准[C++ 异常处理](../cpp/try-throw-and-catch-statements-cpp.md)，Visual C++ 还支持。 使用 C++ 异常处理可以确保你的代码更具可移植性，并且你可以处理任何类型的异常。

如果你有使用 SEH 的 C 代码，可以将它与使用 c + + 异常处理的 c + + 代码中混合。 有关信息，请参阅[处理 c + + 中的结构化的异常](../cpp/exception-handling-differences.md)。

有两种 SEH 机制：

- [异常处理程序](../cpp/writing-an-exception-handler.md)，或 **__except**块，它可以响应或消除异常。

- [终止处理程序](../cpp/writing-a-termination-handler.md)，或 **__finally**始终调用时，无论异常是否导致终止的块。

这两种类型的处理程序是不同的，但会通过称为“展开堆栈”的过程紧密关联。 结构化的异常发生时，Windows 将查找当前处于活动状态的最新安装异常处理程序。 该处理程序可以执行以下三个操作之一：

- 无法识别该异常并将控件传递给其他处理程序。

- 识别异常，但将其消除。

- 识别异常，并处理异常。

识别异常的异常处理程序可能不在异常发生时正在运行的函数中。 在某些情况下，它可能在堆栈上高得多的函数中。 当前正在运行的函数和堆栈帧上的所有其他函数都将终止。 在此过程中，堆栈是"展开"; 即，从堆栈清除非静态局部变量的终止的函数。

当它展开堆栈时，操作系统将调用你为每个函数编写的任何终止处理程序。 通过使用终止处理程序，你可以清理资源，否则资源将由于异常终止而保持打开状态。 如果您已经输入了关键部分，您可以在终止处理程序中退出。 如果程序将要关闭，你可以执行其他维护任务，如关闭和删除临时文件。

## <a name="next-steps"></a>后续步骤

- [编写异常处理程序](../cpp/writing-an-exception-handler.md)

- [编写终止处理程序](../cpp/writing-a-termination-handler.md)

- [处理 C++ 中的结构性异常](../cpp/exception-handling-differences.md)

## <a name="example"></a>示例

如上文所述，析构函数会调用本地对象，如果在 c + + 程序中使用 SEH，并且通过使用对其进行编译的 **/EHa**或 **/EHsc**选项。 但是，如果你也正在使用 C++ 异常，则执行过程中的行为可能不是你所预期的。 此示例演示这些行为差异。

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

如果您使用 **/EHsc**若要编译此代码，但本地测试控件宏`CPPEX`是未定义，则不执行`TestClass`析构函数和输出看起来如下所示：

```Output
Triggering SEH exception
Executing SEH __except block
```

如果你使用 **/EHsc**来编译代码和`CPPEX`使用定义`/DCPPEX`（以致引发 C++ 异常），则`TestClass`析构函数执行并输出如下所示：

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

如果您使用 **/EHa**来编译代码，`TestClass`析构函数执行时不考虑是否使用引发异常`std::throw`或通过使用 SEH 来触发异常，即，是否`CPPEX`定义或不。 输出如下所示：

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

有关详细信息，请参阅 [/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[异常处理](../cpp/exception-handling-in-visual-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
[错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[结构化的异常处理 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)

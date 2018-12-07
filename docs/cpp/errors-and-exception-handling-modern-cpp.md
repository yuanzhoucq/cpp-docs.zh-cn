---
title: 错误和异常处理（现代 C++）
ms.date: 09/17/2018
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: d6192ab800667ceb35bf2e18dcbdc0be95ec70f5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523283"
---
# <a name="errors-and-exception-handling-modern-c"></a>错误和异常处理（现代 C++）

在现代 C++，在大多数情况下，报告和处理逻辑错误和运行时错误的首选的方式是使用异常。 当堆栈可能包含多个函数调用之间检测到错误的函数和具有要知道如何处理它的上下文的函数时，也是如此。 异常提供正式且定义完善的方法的代码检测错误，无法将此信息在调用堆栈中向上传递。

程序错误通常分为两类： 逻辑错误而引起的编程错误，例如、 出错"索引超出范围"和运行时的错误的控制之外的程序员来说，例如，"网络服务不可用"出现错误。 通过返回一个值，表示错误代码或某个特定函数的状态代码或通过设置每个函数调用，以了解后检索调用方的全局变量在 C 样式编程和 COM 中，管理错误报告是否未报告错误。 例如，COM 编程使用 HRESULT 返回值来传递给调用方，错误和 Win32 API 具有 GetLastError 函数来检索已报告的调用堆栈的最后一个错误。 在这种情况下，它由调用方识别代码并相应地作出回应。 如果调用方不显式处理的错误代码，该程序可能会崩溃而不发出警告，或继续使用错误数据执行并生成错误的结果。

由于以下原因，可将异常首选在现代 C++ 中：

- 异常强制调用代码识别错误条件并对其进行处理。 未经处理的异常停止程序执行。

- 异常跳转到能够处理错误的调用堆栈中的点。 中间函数可导致异常传播。 它们不需要与其他层进行协调。

- 异常堆栈展开机制销毁中定义的规则的作用域的所有对象后引发异常。

- 异常将之间检测到错误的代码和处理该错误的代码完全分离。

以下简化的示例显示必要的语法，用于引发和捕获 C++ 中的异常。

```cpp

#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}
```

在 C++ 异常类似于 C# 和 Java 等语言中。 中**尝试**例外情况是如果阻止*引发*它将是*捕获*通过第一个关联的**捕获**其类型与的块异常。 换而言之，执行将从跳**引发**到语句**捕获**语句。 如果找到没有任何可用的 catch 块，则`std::terminate`调用并退出程序。 C++ 中可能会引发任何类型;但是，我们建议您引发派生自的直接或间接类型`std::exception`。 在前面的示例中，异常类型， [invalid_argument](../standard-library/invalid-argument-class.md)，在中的标准库中定义[ \<stdexcept >](../standard-library/stdexcept.md)标头文件。 C + + 不提供，并不需要**最后**块来确保如果引发异常，释放所有资源。 资源获取即是初始化 (RAII) 惯用语法，后者使用智能指针，提供所需的功能的资源清理。 有关详细信息，请参阅[如何： 设计异常安全性](../cpp/how-to-design-for-exception-safety.md)。 有关 C++ 堆栈展开机制的信息，请参阅[异常和堆栈展开](../cpp/exceptions-and-stack-unwinding-in-cpp.md)。

## <a name="basic-guidelines"></a>基本指导原则

可靠的错误处理的方法是具挑战性的任何编程语言。 虽然异常可以提供一些功能，支持好的错误处理功能，它们不能为您做的所有工作。 若要实现的异常机制的好处，请记住异常设计你的代码。

- 使用断言来检查存在应永远不会发生的错误。 使用异常检查可能发生，例如，错误参数的公共函数的输入验证错误。 有关详细信息，请参阅标题为的部分**异常与。断言**。

- 使用异常时处理该错误的代码可能会分开的一个或多个干扰函数调用中检测到错误的代码。 请考虑是否以处理该错误的代码紧密耦合到检测到它的代码时改为使用在性能关键循环中的错误代码。

- 对于每个函数可能会引发或传播异常，提供三种异常保证之一： 增强保证、 基本保证或 nothrow (noexcept) 保证。 有关详细信息，请参阅[如何： 设计异常安全性](../cpp/how-to-design-for-exception-safety.md)。

- 通过值引发异常，通过引用捕获它们。 请勿捕捉无法处理的内容。

- 不要使用异常规范，后者在 C++ 11 中弃用。 有关详细信息，请参阅节**异常规范和 noexcept**。

- 适用时，请使用标准库异常类型。 派生自定义异常类型从[exception 类](../standard-library/exception-class.md)层次结构。

- 不允许异常从析构函数转义或内存释放功能。

## <a name="exceptions-and-performance"></a>异常和性能

异常机制具有极小的性能开销如果不引发任何异常。 如果引发异常，成本的堆栈遍历和展开是大致等于函数调用的成本。 需要额外的数据结构来跟踪调用堆栈后的**尝试**输入块时，和其他说明所需展开堆栈，如果引发异常。 但是，在大多数情况下，在性能和内存占用量的成本并不重要。 性能异常的不利影响，可能需要大量仅在特定内存约束系统上或在性能关键循环中的错误可能会定期发生并且处理它的代码紧密耦合到报告它的代码。 在任何情况下，很可能不进行分析和测量知道异常的实际成本。 即使在这些少数情况下当成本很有意义的您可以权衡它会增加的正确性、 更轻松的可维护性，并通过精心设计的异常策略提供的其他优势。

## <a name="exceptions-vs-assertions"></a>异常与断言

异常和断言是检测程序中运行时错误的两个不同的机制。 使用断言来在应永远不会为您的所有代码是否正确，则返回 true 的开发期间测试条件。 没有任何意义，因为错误表明代码中的某些内容，必须保持不变，使用异常来处理此类错误，并不代表程序已在运行时从恢复的条件。 断言停止执行该语句，以便您可以检查调试器; 中的程序状态异常继续从第一个正确 catch 处理程序的执行。 使用异常检查可能会在运行时，即使你的代码正确，例如，"未找到文件"或"内存不足。"的错误条件 您可能想要恢复由这些情况，即使恢复仅输出到日志消息并结束程序。 始终使用异常检查公共函数的参数。 即使你的函数是无错误的您可能没有完全控制用户传递给它的参数。

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>与 Windows SEH 异常的 C++ 异常

C 和 C++ 程序可使用结构化的异常处理 (SEH) 机制在 Windows 操作系统中。 Seh 的概念类似于 c + + 异常，但使用 SEH **__try**， **__except**，并 **__finally**构造而不是**尝试**并**捕获**。 在 Visual C++，是为 SEH 实现 C++ 异常。 但是，当你编写 C++ 代码，使用 C++ 异常语法。

有关 SEH 的详细信息，请参阅[结构化异常处理 （C/C++）](../cpp/structured-exception-handling-c-cpp.md)。

## <a name="exception-specifications-and-noexcept"></a>异常规范和 noexcept

异常规范的引入了 C++ 中作为一种方式指定函数可能引发的异常。 但是，异常规范事实证明，在实践中，有问题，以及 C++ 11 草稿标准中已弃用。 我们建议你不要使用异常规范除`throw()`，指示的函数使没有异常进行转义。 如果必须使用的类型的异常规范`throw(`*类型*`)`，请注意 Visual C++ 偏离以某些方式的标准。 有关详细信息，请参阅[异常规范 (throw)](../cpp/exception-specifications-throw-cpp.md)。 `noexcept`说明符在 C++ 11 中引入的首选替代作为`throw()`。

## <a name="see-also"></a>请参阅

[如何：异常和非异常代码之间的接口](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
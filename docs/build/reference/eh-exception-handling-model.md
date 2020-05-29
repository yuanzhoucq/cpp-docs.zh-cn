---
title: /EH（异常处理模型）
description: Visual Studio 中 Microsoft C++ /EH（异常处理模型）编译器选项的参考指南。
ms.date: 04/14/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
no-loc:
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396285"
---
# <a name="eh-exception-handling-model"></a>/EH（异常处理模型）

指定编译器生成的异常处理模型支持。 参数指定是否将语法应用于`catch(...)`结构化和标准C++异常、是否**extern假定"C"** 代码为throw异常，以及是否优化某些**noexcept** 检查。

## <a name="syntax"></a>语法

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>参数

**`a`**\
启用标准C++堆叠展开。 使用`catch(...)`语法时，捕获结构化（异步）和标准C++（同步）异常。 **`/EHa`** 重写和**`/EHs`****`/EHc`** 参数。

**`s`**\
启用标准C++堆叠展开。 使用`catch(...)`语法时，仅捕获标准C++异常。 除非**`/EHc`** 还指定，否则编译器假定声明为**extern"C"的**函数可能是throwC++例外。

**`c`**\
当 与**`/EHs`** 中使用 时，编译器假定声明为**extern"C"的**函数永远不会throw成为C++异常。 它与 （即**`/EHa`****`/EHca`** 等效于**`/EHa`**） 一起使用时不起作用。 **`/EHc`** 如果**`/EHs`** 或**`/EHa`** 未指定，则忽略。

**`r`**\
告诉编译器始终为所有**noexcept** 函数生成运行时终止检查。 默认情况下，如果编译器确定函数仅**noexcept** 调用非引发函数，则可能会优化其运行时检查。 此选项提供严格的C++符合性，但代价是一些额外的代码。 **`/EHr`** 如果**`/EHs`** 或**`/EHa`** 未指定，则忽略。

**`-`**\
清除上一个选项参数。 例如，**`/EHsc-`** 被解释为**`/EHs /EHc-`** 和 等效于**`/EHs`**。

**`/EH`** 参数可以按任何顺序单独指定或合并。 如果指定了同一参数的多个实例，则最后一个实例将覆盖任何较早的实例。  **`/EHr- /EHc /EHs`** 例如，**`/EHscr-`** 与 相同，并且**`/EHscr- /EHr`** 具有与**`/EHscr`** 的效果相同。

## <a name="remarks"></a>备注

### <a name="default-exception-handling-behavior"></a>默认异常处理行为

编译器始终生成支持异步结构化异常处理的代码 。SEH 默认情况下（**`/EHsc`** 即，如果没有 ，**`/EHs`** 或**`/EHa`** 指定选项），编译器支持SEH本机C++`catch(...)`子句中的处理程序。 但是，它还生成仅部分支持C++异常的代码。 默认异常展开代码不会销毁由于异常而超出范围的[try](../../cpp/try-throw-and-catch-statements-cpp.md)块之外的自动C++对象。 引发C++异常时，可能会导致资源泄漏和未定义的行为。

### <a name="standard-c-exception-handling"></a>标准C++异常处理

对标准C++异常处理模型的完全编译器支持，该模型安全展开堆栈对象**`/EHsc`** 需要（建议**`/EHs`**）或**`/EHa`**。

如果使用**`/EHs`** 或**`/EHsc`**，则子`catch(...)`句不会catch异步结构化异常。 任何访问冲突和管理<xref:System.Exception?displayProperty=fullName>异常都未捕获。 而且，发生异步异常时作用域中的对象不会销毁，即使代码处理异步异常也是如此。 此行为是使结构化异常未处理的参数。 相反，请考虑这些异常是致命的。

使用**`/EHs`** 或**`/EHsc`** 时，编译器假定异常只能在**throw** 语句或函数调用中发生。 此假设允许编译器消除用于跟踪许多可展开对象的生存期的代码，这可以显著减小代码大小。 如果使用**`/EHa`**，则可执行映像可能会更大、更慢，因为编译器不会像那样积极地优化**try** 块。 它还会在自动清理本地对象的异常筛选器中保留，即使编译器看不到任何可以throwC++异常的代码也是如此。

### <a name="structured-and-standard-c-exception-handling"></a>结构化和标准C++异常处理

编译器**`/EHa`** 选项允许针对异步异常和C++异常进行安全堆栈展开。 它支持使用本机C++`catch(...)`子句处理标准C++和结构化异常。 要实现SEH而不指定**`/EHa`**，可以使用 **__try、__except****__except**和 **__finally**语法。 有关详细信息，请参阅[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md)。

> [!IMPORTANT]
> 使用**`/EHa`** 指定并尝试处理所有异常`catch(...)`可能很危险。 在大多数情况下，异步异常是不可恢复的，因而被认为是致命的。 捕获它们并继续可能导致进程损坏并使 Bug 难以发现和修复。
>
> 即使 Windows 和 Visual SEHC++ 支持，我们强烈建议您使用 ISO 标准C++**`/EHsc`** 异常**`/EHs`** 处理 （或 ）。 它使代码更加便携和灵活。 有时，您仍必须在旧代码或特定SEH类型的程序中使用。 例如，在编译的代码中，它是必需的，以支持通用语言运行时[（/clr](clr-common-language-runtime-compilation.md)）。 有关详细信息，请参阅[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md)。
>
> 我们建议您切勿将使用编译**`/EHa`** 的对象文件链接到使用**`/EHs`** 或**`/EHsc`** 在同一可执行模块中编译的对象文件。 如果必须使用**`/EHa`** 模块中的任意位置来处理异步异常，请使用 编译**`/EHa`** 模块中的所有代码。 您可以在使用 的相同模块中使用结构化异常处理语法，这些代码使用**`/EHs`**。 但是SEH，不能将语法与C++**try** 和**throw****catch** 在同一函数中混合。

如果要**`/EHa`** 使用catch由 以外的内容引发的异常**throw**，请使用 。 以下示例将生成并捕获结构化异常：

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>/clr 下的异常处理

该**`/clr`** 选项表示**`/EHa`**（**`/clr /EHa`** 即冗余）。 如果在**`/EHs`** 中使用 或**`/EHsc`** 后使用，编译器**`/clr`** 将生成错误。 优化不会影响此行为。 捕获异常时，编译器会为与异常位于同一作用域内的任何对象调用类析构函数。 如果未捕获异常，则不运行这些析构函数。

有关 下**`/clr`** 异常处理限制的信息，请参阅[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

### <a name="runtime-exception-checks"></a>运行时异常检查

该**`/EHr`** 选项强制在具有**noexcept** 属性的所有函数中检查运行时终止。 默认情况下，如果编译器后端确定函数仅调用*非引发*函数，则运行时检查可能会被优化。 非引发函数是具有一个指定不会引发任何异常的属性的函数。 它们**noexcept** 包括标记为 的`throw()`函数`__declspec(nothrow)`，和**`/EHc`**，指定时**extern，"C"** 函数。 非引发函数还包括编译器已通过检查确定为非引发的任何函数。 可以使用 显式设置默认行为**`/EHr-`**。

非引发属性不能保证函数不能引发异常。 与**noexcept** 函数的行为不同，MSVC 编译器将使用`throw()``__declspec(nothrow)`**extern** 声明的函数引发的异常视为未定义的行为。 使用这三个声明属性的函数不强制运行时终止检查异常。 可以使用 该**`/EHr`** 选项通过强制编译器为转义**noexcept** 函数的未处理异常生成运行时检查来帮助标识此未定义的行为。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在可视化工作室中设置选项，或以编程方式设置选项

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/C++** > **代码生成**。

1. 修改 **“启用 C++ 异常”** 属性。

   或者，将 **“启用 C++ 异常”** 设置为 **“No”**，然后在 **“命令行”** 属性页中的 **“附加选项”** 框中键入编译选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)\
[错误和异常处理](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[例外规格throw（ ）](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

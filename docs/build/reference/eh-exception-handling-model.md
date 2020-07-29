---
title: /EH（异常处理模型）
description: Visual Studio 中的 Microsoft c + +/EH （异常处理模型）编译器选项的参考指南。
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
- ':::no-loc(SEH):::'
- ':::no-loc(try):::'
- ':::no-loc(catch):::'
- ':::no-loc(throw):::'
- ':::no-loc(extern):::'
- ':::no-loc(finally):::'
- ':::no-loc(noexcept):::'
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: f158e951d595d5934ff513254871710db5920bf1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232711"
---
# <a name="eh-exception-handling-model"></a>/EH（异常处理模型）

指定编译器生成的异常处理模型支持。 参数指定是否将 `:::no-loc(catch):::(...)` 语法应用到结构化和标准 c + + 异常，是否假定** :::no-loc(extern)::: "C"** 代码为 :::no-loc(throw)::: 异常以及是否优化掉某些 **`:::no-loc(noexcept):::`** 检查。

## <a name="syntax"></a>语法

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>参数

**`a`**\
启用标准 c + + 堆栈展开。 使用语法时捕获结构化（异步）和标准 c + + （同步）异常 `:::no-loc(catch):::(...)` 。 **`/EHa`** 重写 **`/EHs`** 和 **`/EHc`** 参数。

**`s`**\
启用标准 c + + 堆栈展开。 使用语法时仅捕获标准 c + + 异常 `:::no-loc(catch):::(...)` 。 除非 **`/EHc`** 还指定，否则编译器假定声明为** :::no-loc(extern)::: "C"** 的函数可能 :::no-loc(throw)::: 是 c + + 异常。

**`c`**\
当与一起使用时 **`/EHs`** ，编译器假定声明为** :::no-loc(extern)::: "c"** 的函数从不 :::no-loc(throw)::: 出现 c + + 异常。 与 **`/EHa`** （即 **`/EHca`** 等效于）一起使用时，它不起作用 **`/EHa`** 。 **`/EHc`** 如果未指定或，则忽略 **`/EHs`** **`/EHa`** 。

**`r`**\
告知编译器始终为所有函数生成运行时终止检查 **`:::no-loc(noexcept):::`** 。 默认情况下， **`:::no-loc(noexcept):::`** 如果编译器确定该函数仅调用非 ing 函数，则的运行时检查可能被优化掉 :::no-loc(throw)::: 。 此选项为严格的 c + + 一致性提供了一些额外代码。 **`/EHr`** 如果未指定或，则忽略 **`/EHs`** **`/EHa`** 。

**`-`**\
清除上一个选项参数。 例如， **`/EHsc-`** 将解释为 **`/EHs /EHc-`** ，且等效于 **`/EHs`** 。

**`/EH`** 可以按任意顺序单独或组合指定参数。 如果指定了同一自变量的多个实例，则最后一个实例将覆盖任何以前的实例。  例如，与 **`/EHr- /EHc /EHs`** 相同 **`/EHscr-`** ，其 **`/EHscr- /EHr`** 效果与相同 **`/EHscr`** 。

## <a name="remarks"></a>备注

### <a name="default-exception-handling-behavior"></a>默认异常处理行为

编译器始终生成支持异步结构化异常处理（）的代码 :::no-loc(SEH)::: 。 默认情况下（即，如果未 **`/EHsc`** **`/EHs`** 指定、或 **`/EHa`** 选项），则编译器支持 :::no-loc(SEH)::: 本机 c + + 子句中的处理程序 `:::no-loc(catch):::(...)` 。 但是，它还会生成仅部分支持 c + + 异常的代码。 默认异常展开代码不会销毁由于异常而超出范围的块外的自动 c + + 对象 [:::no-loc(try):::](../../cpp/:::no-loc(try):::-:::no-loc(throw):::-and-:::no-loc(catch):::-statements-cpp.md) 。 C + + 异常为 n 时，可能会导致资源泄漏和未定义的行为 :::no-loc(throw)::: 。

### <a name="standard-c-exception-handling"></a>标准 c + + 异常处理

对安全地展开堆栈对象的标准 c + + 异常处理模型的完全编译器支持 **`/EHsc`** （推荐）、 **`/EHs`** 或 **`/EHa`** 。

如果使用 **`/EHs`** 或 **`/EHsc`** ，则 `:::no-loc(catch):::(...)` 子句不会 :::no-loc(catch)::: 异步构造异常。 任何访问冲突和托管 <xref:System.Exception?displayProperty=fullName> 异常均不会被捕获。 而且，发生异步异常时，范围内的对象不会被销毁，即使代码处理异步异常也是如此。 此行为是将结构化异常保持未处理的参数。 相反，请考虑这些异常。

使用或时 **`/EHs`** **`/EHsc`** ，编译器将假定异常只能出现在 **`:::no-loc(throw):::`** 语句或函数调用中。 此假设允许编译器消除跟踪许多不可展开对象生存期的代码，这可能会显著降低代码大小。 如果使用 **`/EHa`** ，可执行映像可能会更大且更慢，因为编译器不会 **`:::no-loc(try):::`** 主动优化块。 它还保留在自动清理本地对象的异常筛选器中，即使编译器未看到任何可能 :::no-loc(throw)::: 出现 c + + 异常的代码也是如此。

### <a name="structured-and-standard-c-exception-handling"></a>结构化和标准 c + + 异常处理

**`/EHa`** 编译器选项为异步异常和 c + + 异常启用安全堆栈展开。 它支持使用本机 c + + 子句处理标准 c + + 和结构化异常 `:::no-loc(catch):::(...)` 。 若要 :::no-loc(SEH)::: 在不指定的情况 **`/EHa`** 下实现，可以使用 **__ :::no-loc(try)::: **、 **`__except`** 和 **`__:::no-loc(finally):::`** 语法。 有关详细信息，请参阅[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md)。

> [!IMPORTANT]
> 使用来指定 **`/EHa`** :::no-loc(try)::: 处理所有异常的和 ing `:::no-loc(catch):::(...)` 可能很危险。 在大多数情况下，异步异常是不可恢复的，因而被认为是致命的。 捕获它们并继续可能导致进程损坏并使 Bug 难以发现和修复。
>
> 即使 Windows 和 Visual C++ 支持 :::no-loc(SEH)::: ，我们也强烈建议使用 ISO 标准 c + + 异常处理（ **`/EHsc`** 或 **`/EHs`** ）。 它使你的代码更具可移植性和灵活性。 可能仍然需要使用 :::no-loc(SEH)::: 旧代码或特定类型的程序。 例如，在编译的代码中需要用来支持公共语言运行时（[/clr](clr-common-language-runtime-compilation.md)）。 有关详细信息，请参阅[结构化异常处理](../../cpp/structured-exception-handling-c-cpp.md)。
>
> 建议你不要将使用编译的对象文件链接 **`/EHa`** 到使用 **`/EHs`** 或 **`/EHsc`** 在同一可执行模块中编译的对象。 如果你必须使用模块中的任何位置来处理异步异常 **`/EHa`** ，请使用 **`/EHa`** 来编译模块中的所有代码。 您可以在与使用编译的代码相同的模块中使用结构化异常处理语法 **`/EHs`** 。 但是，不能 :::no-loc(SEH)::: **`:::no-loc(try):::`** **`:::no-loc(throw):::`** **`:::no-loc(catch):::`** 在同一函数中将语法与 c + +、和混合使用。

**`/EHa`** 如果你想要 :::no-loc(catch)::: 执行由之外的内容引发的异常，请使用 **`:::no-loc(throw):::`** 。 此示例生成 :::no-loc(catch)::: 结构化异常，并为其生成：

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to :::no-loc(catch)::: it using :::no-loc(catch):::(...)
    :::no-loc(try):::
    {
        int i = 0, j = 1;
        j /= i;   // This will :::no-loc(throw)::: a SE (divide by zero).
        printf("%d", j);
    }
    :::no-loc(catch):::(...)
    {
        // :::no-loc(catch)::: block will only be executed under /EHa
        cout << "Caught an exception in :::no-loc(catch):::(...)." << endl;
    }
}

int main()
{
    __:::no-loc(try):::
    {
        fail();
    }

    // __except will only :::no-loc(catch)::: an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the :::no-loc(catch):::(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>/Clr 下的异常处理

**`/clr`** 选项隐含 **`/EHa`** （即， **`/clr /EHa`** 是冗余的）。 如果 **`/EHs`** **`/EHsc`** 在之后使用了或，则编译器将生成错误 **`/clr`** 。 优化不会影响此行为。 捕获到异常时，编译器将为与该异常位于同一范围内的任何对象调用类析构函数。 如果未捕获到异常，则不会运行这些析构函数。

有关下的异常处理限制的信息 **`/clr`** ，请参阅[_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

### <a name="runtime-exception-checks"></a>运行时异常检查

**`/EHr`** 选项在具有属性的所有函数中强制运行时终止检查 **`:::no-loc(noexcept):::`** 。 默认情况下，如果编译器后端确定某个函数仅调用*非 :::no-loc(throw)::: ing*函数，则运行时检查可能被优化掉。 非 :::no-loc(throw)::: ing 函数是任何具有指定 no 异常的属性的函数都可能是 :::no-loc(throw)::: n。 它们包括标记为、、和的函数（ **`:::no-loc(noexcept):::`** `:::no-loc(throw):::()` `__declspec(no:::no-loc(throw):::)` 在 **`/EHc`** 指定时，为** :::no-loc(extern)::: "C"** 函数）。 非 :::no-loc(throw)::: ing 函数还包括编译器已通过检查确定为非 ing 的任何函数 :::no-loc(throw)::: 。 您可以使用显式设置默认行为 **`/EHr-`** 。

非 :::no-loc(throw)::: ing 特性并不保证函数的异常不能是 :::no-loc(throw)::: n。 与函数的行为不同 **`:::no-loc(noexcept):::`** ，MSVC 编译器会 :::no-loc(throw)::: 通过使用 `:::no-loc(throw):::()` 、 `__declspec(no:::no-loc(throw):::)` 或** :::no-loc(extern)::: "C"** 声明为未定义行为的函数来考虑异常 n。 使用这三个声明属性的函数不会对异常强制运行时终止检查。 你可以使用 **`/EHr`** 选项来帮助你确定此未定义的行为，方法是强制编译器为转义函数的未处理异常生成运行时检查 **`:::no-loc(noexcept):::`** 。

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>在 Visual Studio 中或以编程方式设置选项

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **代码生成**"。

1. 修改 **“启用 C++ 异常”** 属性。

   或者，将 **“启用 C++ 异常”** 设置为 **“No”**，然后在 **“命令行”** 属性页中的 **“附加选项”** 框中键入编译选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)\
[错误和异常处理](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[异常规范（ :::no-loc(throw)::: ）](../../cpp/exception-specifications-:::no-loc(throw):::-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

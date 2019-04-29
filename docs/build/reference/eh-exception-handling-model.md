---
title: /EH（异常处理模型）
ms.date: 08/14/2018
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
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 9f5eed60ecb51abc1d8fbd3c38773bbf782b23a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271796"
---
# <a name="eh-exception-handling-model"></a>/EH（异常处理模型）

指定当编译器使用的异常处理类型、何时优化掉异常检查以及是否销毁由于异常而超出范围的 C++ 对象。 如果 **/EH**未指定，编译器使代码能够捕获这两个异步结构化的异常和C++异常，但不会销毁C++由于异步异常超出范围的对象。

## <a name="syntax"></a>语法

> **/EH**{**s**|**a**}[**c**][**r**][**-**]

## <a name="arguments"></a>自变量

**a**<br/>
异常处理模型同时捕获异步 （结构化） 和同步 (C++) 异常按使用的C++`catch(...)`语法。

**s**<br/>
捕获同步异常处理模型 (C++) 仅异常并通知编译器假定函数声明为**extern"C"** 可能会引发异常。

**c**<br/>
如果用于**s** (**/EHsc**)，会捕获C++仅异常并通知编译器假定函数声明为**extern"C"** 永远不会引发C++异常。 **/EHca** 与 **/EHa**相等。

**r**<br/>
告知编译器始终生成运行时终止检查所有**noexcept**函数。 默认情况下，运行时检查**noexcept**可能被优化掉如果编译器确定该函数调用仅非引发函数。

## <a name="remarks"></a>备注

 **/EHa** 编译器选项用于支持使用本机 C++ `catch(...)` 子句的异步结构化异常处理 (SEH)。 不指定情况下实现 SEH **/EHa**，可以使用 **__try**， **__except**，以及 **__finally**语法。 尽管 Windows 和 Visual C++ 支持 SEH，但强烈建议你使用 ISO 标准 C++ 异常处理（**/EHs** 或 **/EHsc**），因为它使代码更可移植并更灵活。 不过，在现有代码或为特定类型的程序 — 例如，在代码编译为支持公共语言运行时 ([/clr （公共语言运行时编译）](clr-common-language-runtime-compilation.md)) — 您仍可能必须使用 SEH。 有关详细信息，请参阅 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。

指定 **/EHa** 并尝试使用 `catch(...)` 处理所有异常可能很危险。 在大多数情况下，异步异常是不可恢复的，因而被认为是致命的。 捕获它们并继续可能导致进程损坏并使 Bug 难以发现和修复。

如果使用 **/EHs** 或 **/EHsc**，则 `catch(...)` 子句不会捕捉异步结构化异常。 将捕获不到访问冲突和托管 <xref:System.Exception?displayProperty=fullName> 异常，并且范围内的对象产生了异步异常也不会被销毁（即使异步异常已处理）。

如果您使用 **/EHa**，映像可能较大且性能较低因为编译器不优化**尝试**同样积极地阻止。 并且它留在自动调用所有本地对象的析构函数的异常筛选器中（即使编译器未看到可引发 C++ 异常的任何代码）。 这使你可以为异步异常和 C++ 异常展开安全堆栈。 当你使用 **/EHs**，则编译器假定异常才会出现在**引发**语句或函数调用。 这使编译器能够消除代码以跟踪很多不可展开对象的生存期，并且这也能显著减小代码大小。

我们建议不链接使用编译的对象 **/EHa**与使用编译的对象一起 **/EHs**或 **/EHsc**相同的可执行模块中。 如果必须通过在模块中的任意位置使用 **/EHa** 来处理异步异常，请在此模块中使用 **/EHa** 来编译所有代码。 可以使用结构化的异常处理中使用已编译的代码相同的模块的语法 **/EHs**，但不能将 SEH 语法与混合**尝试**，**引发**，和**捕获**在同一函数中。

使用 **/EHa**如果你想要捕获由某些内容而不引发异常**引发**。 以下示例将生成并捕获结构化异常：

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

**/EHc** 选项需要指定 **/EHs** 或 **/EHa** 。 **/Clr**选项暗指 **/EHa** (即 **/clr** **/EHa**是冗余的)。 如果编译器将生成错误 **/EHs**或 **/EHsc**后使用 **/clr**。 优化不会影响此行为。 当捕获到某个异常时，编译器将为与该异常在同一范围内的对象调用类析构函数。 如果未捕获到异常，则不会运行这些析构函数。

有关 **/clr**下的异常处理限制的信息，请参见 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。

可以使用符号 **-** 清除该选项。 例如， **/EHsc-** 被解释为 **/EHs** **/EHc-** ，等效于 **/EHs**。

**/EHr**编译器选项将强制具有的所有函数中的运行时终止检查**noexcept**属性。 默认情况下，如果编译器后端确定该函数仅调用 *非引发* 函数，则运行时检查可能被优化掉。 非引发函数是具有一个指定不会引发任何异常的属性的函数。 这包括标记的函数**noexcept**， `throw()`， `__declspec(nothrow)`，以及何时**了 /EHc**指定，则**extern"C"** 函数。 非引发函数还包括编译器已通过检查确定为非引发的任何函数。 可以通过使用 **/EHr-** 显式设置默认值。

但是，非引发属性不保证函数不会引发任何异常。 与不同的行为**noexcept**函数，MSVC 编译器会考虑通过使用声明的函数引发的异常`throw()`， `__declspec(nothrow)`，或**extern"C"** 作为未定义的行为。 使用这三个声明属性的函数不强制使用运行时终止检查确定是否存在异常。 可以使用 **/EHr**选项，可帮助你确定此未定义行为，通过强制编译器生成的转义的未经处理异常的运行时检查**noexcept**函数。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C /C++** > **代码生成**。

1. 修改 **“启用 C++ 异常”** 属性。

   或者，将 **“启用 C++ 异常”** 设置为 **“No”**，然后在 **“命令行”** 属性页中的 **“附加选项”** 框中键入编译选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[错误和异常处理](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[结构化异常处理 (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

---
title: -EH （异常处理模型） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
dev_langs:
- C++
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96b009a9f209ffcc4bb84550c5f37680ef71c9fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="eh-exception-handling-model"></a>/EH（异常处理模型）
指定当编译器使用的异常处理类型、何时优化掉异常检查以及是否销毁由于异常而超出范围的 C++ 对象。 如果未指定 **/EH** ，则编译器将同时捕获异步结构化异常和 C++ 异常，但不会销毁由于异步异常超出范围的 C++ 对象。  
  
## <a name="syntax"></a>语法  
  
```  
/EH{s|a}[c][r][-]  
```  
  
## <a name="arguments"></a>自变量  
 **a**  
 同时捕获异步（结构化）和同步 (C++) 异常的异常处理模型。  
  
 **s**  
 仅捕获 C++ 异常并通知编译器假定声明为 `extern "C"` 的函数可能引发异常的异常处理模型。  
  
 **c**  
 如果与 **s** (**/EHsc**) 一起使用，则仅捕获 C++ 异常并通知编译器假定声明为 `extern "C"` 的函数从未引发 C++ 异常。  
  
 **/EHca** 与 **/EHa**相等。  
  
 **r**  
 告知编译器始终为所有 `noexcept` 函数生成运行时终止检查。 默认情况下，如果编译器确定该函数仅调用非引发函数，则运行时检查 `noexcept` 可能被优化掉。  
  
## <a name="remarks"></a>备注  
 **/EHa** 编译器选项用于支持使用本机 C++ `catch(...)` 子句的异步结构化异常处理 (SEH)。 若要在不指定 **/EHa**的情况下实现 SEH，则可以使用 `__try`, `__except`和 `__finally` 语法。 尽管 Windows 和 Visual C++ 支持 SEH，但强烈建议你使用 ISO 标准 C++ 异常处理（**/EHs** 或 **/EHsc**），因为它使代码更可移植并更灵活。 但是，在现有代码中或对于特定类型的程序 — 例如，在代码编译为支持公共语言运行时 ([/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)) — 你仍可能必须使用 SEH。 有关详细信息，请参阅 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 指定 **/EHa** 并尝试使用 `catch(...)` 处理所有异常可能很危险。 在大多数情况下，异步异常是不可恢复的，因而被认为是致命的。 捕获它们并继续可能导致进程损坏并使 Bug 难以发现和修复。  
  
 如果使用 **/EHs** 或 **/EHsc**，则 `catch(...)` 子句不会捕捉异步结构化异常。 将捕获不到访问冲突和托管 <xref:System.Exception?displayProperty=fullName> 异常，并且范围内的对象产生了异步异常也不会被销毁（即使异步异常已处理）。  
  
 如果使用 **/EHa**，则映像可能较大且性能较低，因为编译器不会同样积极地优化 `try` 块。 并且它留在自动调用所有本地对象的析构函数的异常筛选器中（即使编译器未看到可引发 C++ 异常的任何代码）。 这使你可以为异步异常和 C++ 异常展开安全堆栈。 当你使用 **/EHs**时，编译器假定异常只在 `throw` 语句或函数调用处发生。 这使编译器能够消除代码以跟踪很多不可展开对象的生存期，并且这也能显著减小代码大小。  
  
 建议你不要在同一可执行模块中将使用 **/EHa** 编译的对象与使用 **/EHs** 编译的对象链接在一起。 如果必须通过在模块中的任意位置使用 **/EHa** 来处理异步异常，请在此模块中使用 **/EHa** 来编译所有代码。 可在与使用 **/EHs**编译的代码相同的模块中使用结构化异常处理语法，但不能将 SEH 语法与同一函数中的 `try`, `throw`和 `catch` 混合。  
  
 如果要捕获由 **/EHa** 以外的内容引发的异常，请使用 `throw`相等。 以下示例将生成并捕获结构化异常：  
  
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
  
 **/EHc** 选项需要指定 **/EHs** 或 **/EHa** 。 **/clr** 选项暗指 **/EHa** （即 **/clr /EHa** 是冗余的）。 如果在 **/EHs[c]** 后使用 **/clr**，编译器将产生一个错误。 优化不会影响此行为。 当捕获到某个异常时，编译器将为与该异常在同一范围内的对象调用类析构函数。 如果未捕获到异常，则不会运行这些析构函数。  
  
 有关 **/clr**下的异常处理限制的信息，请参见 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。  
  
 可以使用符号 **-** 清除该选项。 例如， **/EHsc-** 解释为 **/EHs /EHc-** 并且等效于 **/EHs**。  
  
 **/EHr** 编译器选项将在具有 `noexcept` 属性的所有函数中强制运行时终止检查。 默认情况下，如果编译器后端确定该函数仅调用 *非引发* 函数，则运行时检查可能被优化掉。 非引发函数是具有一个指定不会引发任何异常的属性的函数。 这包括标记为 `noexcept`, `throw()`, `__declspec(nothrow)`的函数，当指定了 **/EHc** 时，还包括 `extern "C"` 函数生成运行时终止检查。 非引发函数还包括编译器已通过检查确定为非引发的任何函数。 可以通过使用 **/EHr-** 显式设置默认值。  
  
 但是，非引发属性不保证函数不会引发任何异常。 与 `noexcept` 函数的行为不同，Visual C++ 编译器认为使用 `throw()`、 `__declspec(nothrow)`或 `extern "C"` 声明的函数引发的异常是未定义的行为。 使用这三个声明属性的函数不强制使用运行时终止检查确定是否存在异常。 可以通过强制编译器为逸出 **/EHr** 函数的未处理异常生成运行时检查，使用 `noexcept` 选项帮助你确定此未定义的行为。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展开“配置属性” 、“C/C++” 和“代码生成” 。  
  
3.  修改 **“启用 C++ 异常”** 属性。  
  
     或者，将 **“启用 C++ 异常”** 设置为 **“No”**，然后在 **“命令行”** 属性页中的 **“附加选项”** 框中键入编译选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [错误和异常处理](../../cpp/errors-and-exception-handling-modern-cpp.md)   
 [异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [结构化异常处理 (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
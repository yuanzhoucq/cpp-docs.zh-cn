---
title: -RTC （运行时错误检查） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
dev_langs:
- C++
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8699a96dcd7c04bc1b2707e964afb4b68068147e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="rtc-run-time-error-checks"></a>/RTC（运行时错误检查）
用于启用和禁用运行时错误检查功能，结合[runtime_checks](../../preprocessor/runtime-checks.md)杂注。  
  
## <a name="syntax"></a>语法  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## <a name="arguments"></a>自变量  
 `1`  
 等效的**/RTC**`su`。  
  
 `c`  
 报表值时被分配给较小的数据类型和数据丢失的结果。 例如，如果类型的值`short 0x101`分配给类型的变量的`char`。  
  
 此选项将报告打算在其中你截断，例如，如果您希望的第一个八位的情况下`int`作为返回`char`。 因为**/RTC** `c`导致运行时错误，如果赋值而丢失任何信息，你可以关闭需要避免运行时错误的结果的信息来屏蔽**/RTC** `c`. 例如:  
  
```  
#include <crtdbg.h>  
  
char get8bits(int value, int position) {  
   _ASSERT(position < 32);  
   return (char)(value >> position);  
   // Try the following line instead:  
   // return (char)((value >> position) & 0xff);  
}  
  
int main() {  
   get8bits(12341235,3);  
}  
```  
  
 `s`  
 启用堆栈帧运行时错误检查，，如下所示：  
  
-   为非零值的本地变量的初始化。 这有助于识别在调试模式下运行时不会出现的 bug。 没有堆栈变量将仍为调试版本相比由于堆栈中的变量的发布版本的编译器优化的发布版本中的零的可能性更大。 程序已用完其堆栈的区域，一旦它永不会重置为 0 由编译器。 因此，发生这种情况使用相同的堆栈区域的后续、 未经初始化即堆栈变量可以返回从之前的此堆栈内存使用留下的值。  
  
-   检测到的本地变量，例如数组的溢出和不足。 **/RTC** `s`访问结构中的编译器填充导致的内存时将不会检测溢出。 通过使用可能发生填充[对齐](../../cpp/align-cpp.md)， [/Zp （结构成员对齐）](../../build/reference/zp-struct-member-alignment.md)，或[包](../../preprocessor/pack.md)，或如果结构元素进行排序的方式要求编译器以添加填充。  
  
-   堆栈指针验证，检测到堆栈指针损坏。 可以通过调用约定不匹配导致堆栈指针损坏。 例如，使用函数指针，则调用中的函数都将作为导出的 DLL [__stdcall](../../cpp/stdcall.md)但声明作为函数指针[__cdecl](../../cpp/cdecl.md)。  
  
 `u`  
 报告何时不具有已初始化的情况下使用变量。 例如，生成一个指令`C4701`也可能生成下的一个运行时错误**/RTC**`u`。 生成的任何指令[编译器警告 （等级 1 和等级 4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)将生成下的运行时错误**/RTC**`u`。  
  
 但是，考虑下面的代码片段：  
  
```cpp  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 如果变量可能已初始化，它将不会报告在运行时**/RTC**`u`。 例如，通过指针使用别名变量后，编译器将不跟踪变量和报告未初始化的使用。 实际上，你可以通过获取它的地址初始化变量。 在这种情况下，&运算符的作用类似于赋值运算符。  
  
## <a name="remarks"></a>备注  
 运行时错误检查是一种方法供你在运行中的代码; 中找到问题有关详细信息，请参阅[如何： 使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)。  
  
 如果在编译时在命令行使用任一程序**/RTC**编译器选项、 任何杂注[优化](../../preprocessor/optimize.md)在代码中的说明将以静默方式失败。 这是因为运行时错误检查 （已优化） 的发行版中不可用。  
  
 应使用**/RTC**对于开发生成;**/RTC**不应该用于零售版本。 **/RTC**不能用于编译器优化 ([/O 选项 （优化代码）](../../build/reference/o-options-optimize-code.md))。 使用生成的程序映像**/RTC**稍大一些，比使用生成的映像稍慢将**/Od** (低于最多 5% **/Od**生成)。  
  
 当你使用任何时，将定义 __MSVC_RUNTIME_CHECKS 预处理器指令**/RTC**选项或[/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**代码生成**属性页。  
  
4.  修改一个或两个以下属性：**基本运行时检查**或**较小的类型检查**。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 属性。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)
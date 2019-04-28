---
title: /RTC（运行时错误检查）
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
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
ms.openlocfilehash: a830ff5b8ba4b7fcd95eb462f899f2eadce6de11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318545"
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

**1**<br/>
等效 **/RTC**`su`。

**c**<br/>
报表的值时分配给较小的数据类型，而导致数据丢失。 例如，如果类型的值`short 0x101`分配给类型的变量的`char`。

此选项将报告在其中你想要截断，例如，如果您希望的第一个八位的情况下`int`作为返回`char`。 因为 **/RTC** `c`会导致运行时错误赋值后导致丢失任何信息时，可屏蔽，以避免运行时错误导致的所需的信息 **/RTC** `c`. 例如：

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

**s**<br/>
启用堆栈帧运行时错误检查，如下所示：

- 为非零值的本地变量的初始化。 这有助于找出在调试模式下运行时不会出现的 bug。 没有堆栈变量仍将为在调试版本中相比发布版本由于堆栈中的变量的发布版本的编译器优化的零的可能性更大。 后一个程序已用完其堆栈的一个区域，它永远不会重置为 0 的编译器。 因此，碰巧使用相同的堆栈区域的后续、 未初始化堆栈变量可以返回先前使用此堆栈内存中剩余的值。

- 检测到的本地变量，如数组的溢出和不足。 **/RTC** `s`访问编译器填充在结构中导致的内存时将不会检测溢出。 通过使用可能发生填充[对齐](../../cpp/align-cpp.md)， [/Zp （结构成员对齐）](zp-struct-member-alignment.md)，或[pack](../../preprocessor/pack.md)，或如果要求编译器添加空白的方式对结构元素。

- 堆栈指针验证，检测到堆栈指针损坏。 堆栈指针损坏可能引起调用约定不匹配。 例如，使用函数指针，则调用函数中作为导出的 DLL [__stdcall](../../cpp/stdcall.md)声明为函数的指针，但[__cdecl](../../cpp/cdecl.md)。

**u**<br/>
当不具有已初始化的情况下使用变量时报告。 例如，将生成一个指令`C4701`也可能生成下的一个运行时错误 **/RTC**`u`。 生成的任何指令[编译器警告 （等级 1 和 4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)将生成下的一个运行时错误 **/RTC**`u`。

但是，考虑下面的代码段：

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

如果变量可能已初始化，它将不会报告在运行时 **/RTC**`u`。 例如，变量是通过指针使用别名后，编译器将不跟踪变量并报告未初始化的使用。 实际上，您可以通过获取它的地址初始化变量。 & 运算符工作方式类似于在此情况下的赋值运算符。

## <a name="remarks"></a>备注

运行时错误检查是一种方法，以便查找你正在运行的代码; 中的问题有关详细信息，请参阅[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)

如果您编译你的程序在命令行使用任一 **/RTC**编译器选项、 任何杂注[优化](../../preprocessor/optimize.md)在代码中的说明将以静默方式失败。 这是因为运行时错误检查 （已优化） 的发布版本中无效。

应使用 **/RTC**的开发内部版本;**/RTC**不应该用于零售版本。 **/RTC**不能用于编译器优化 ([/O 选项 （优化代码）](o-options-optimize-code.md))。 使用生成的程序映像 **/RTC**稍大一些，使用生成的映像相比，速度稍慢 **/Od** (低于最多 5% **/Od**生成)。

当你使用任何将定义 __MSVC_RUNTIME_CHECKS 预处理器指令 **/RTC**选项或[/GZ](gz-enable-stack-frame-run-time-error-checking.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**代码生成**属性页。

1. 修改一个或两个以下属性：**基本运行时检查**或**较小的类型检查**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 属性。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)

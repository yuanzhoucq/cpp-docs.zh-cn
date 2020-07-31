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
ms.openlocfilehash: 49f0e4bace5f3dd199b58854e838204bd2cd5f3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222012"
---
# <a name="rtc-run-time-error-checks"></a>/RTC（运行时错误检查）

用于启用和禁用运行时错误检查功能，与[runtime_checks](../../preprocessor/runtime-checks.md)杂注一起使用。

## <a name="syntax"></a>语法

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>参数

**1**<br/>
与 **/rtc**等效 `su` 。

**ansi-c**<br/>
报告何时向较小的数据类型分配值并导致数据丢失。 例如，如果将类型的值 `short 0x101` 分配给类型的变量，则为 **`char`** 。

此选项报告你打算截断的情况，例如，如果你想要将作为返回的的前八位 **`int`** **`char`** 。 由于 **/RTC** `c` 在赋值后丢失了任何信息，因此，当/rtc 导致运行时错误时，可以屏蔽所需的信息，以避免由于 **/rtc**导致运行时错误 `c` 。 例如：

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

**些**<br/>
启用堆栈帧运行时错误检查，如下所示：

- 将局部变量初始化为一个非零值。 这有助于识别在调试模式下运行时未出现的 bug。 与发布版本相比，在调试版本中，堆栈变量在调试版本中仍将保持为零，因为对发布版本中的堆栈变量进行编译器优化。 一旦某个程序使用了其堆栈的区域，编译器将永远不会将其重置为0。 因此，接下来使用同一堆栈区的未初始化的堆栈变量可以返回以前使用此堆栈内存时留下的值。

- 检测局部变量（如数组）的溢出和不足。 **/Rtc** `s`当访问在结构内由编译器填充生成的内存时，将不会检测溢出。 可以通过使用[align](../../cpp/align-cpp.md)、 [/Zp （结构成员对齐）](zp-struct-member-alignment.md)或[pack](../../preprocessor/pack.md)，或如果按要求编译器添加填充的方式对结构元素进行排序，进行填充。

- 堆栈指针验证，检测堆栈指针损坏。 堆栈指针损坏可能是由于调用约定不匹配造成的。 例如，使用函数指针时，会调用 DLL 中的一个函数，该函数作为[__stdcall](../../cpp/stdcall.md)导出，但您将该函数的指针声明为[__cdecl](../../cpp/cdecl.md)。

**u**<br/>
报告在没有初始化的情况下使用变量的时间。 例如，生成的指令 `C4701` 可能还会在 **/rtc**下生成运行时错误 `u` 。 任何生成[编译器警告（等级1和等级4） C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)的指令将在/rtc 下生成运行时错误 **/RTC** `u` 。

不过，请考虑以下代码片段：

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

如果变量可能已初始化，则将不会在运行时通过/Rtc 报告它 **/RTC** `u` 。 例如，变量通过指针化名后，将不会跟踪该变量并报告未初始化的使用情况。 实际上，可以通过获取变量的地址来初始化变量。 在这种情况下，& 运算符的工作方式类似于赋值运算符。

## <a name="remarks"></a>备注

通过运行时错误检查，你可以在运行代码中查找问题;有关详细信息，请参阅[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)。

如果使用任何 **/rtc**编译器选项在命令行编译程序，则代码中的所有 pragma[优化](../../preprocessor/optimize.md)指令都将以静默方式失败。 这是因为运行时错误检查在发布（优化）版本中无效。

应将 **/rtc**用于开发生成;不应将 **/rtc**用于零售版本。 **/Rtc**不能与编译器优化一起使用（[/O 选项（优化代码）](o-options-optimize-code.md)）。 使用 **/rtc**构建的程序映像将略大一些，比使用 **/od**构建的映像（比 **/od**版本慢5%）要慢得多。

当你使用任何 **/rtc**选项或[/GZ](gz-enable-stack-frame-run-time-error-checking.md)时，将定义 __MSVC_RUNTIME_CHECKS 预处理器指令。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击 "**代码生成**" 属性页。

1. 修改以下一个或两个属性：**基本运行时检查**或**更小的类型检查**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 属性。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[如何：使用本机运行时检查](/visualstudio/debugger/how-to-use-native-run-time-checks)

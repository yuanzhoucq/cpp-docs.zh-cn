---
title: /Gd、/Gr、/Gv、/Gz（调用约定）
ms.date: 09/05/2018
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: 8eba665e34fc3b949283557461e33348106fd532
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451500"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd、/Gr、/Gv、/Gz（调用约定）

这些选项用于确定函数参数推送到堆栈上，是否从末尾的调用堆栈的调用方函数或被调用的函数移除参数的顺序以及编译器用来标识的名称修饰约定各个函数。

## <a name="syntax"></a>语法

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**<br/>

## <a name="remarks"></a>备注

**/Gd**，默认设置，指定[__cdecl](../../cpp/cdecl.md)函数和函数以及标记为除 c + + 成员以外的所有函数调用约定[__stdcall](../../cpp/stdcall.md)， [__fastcall](../../cpp/fastcall.md)，或[__vectorcall](../../cpp/vectorcall.md)。

**/Gr**指定`__fastcall`除 c + + 成员函数的所有函数的调用约定，函数名为`main`，和标记的函数`__cdecl`， `__stdcall`，或`__vectorcall`。 所有`__fastcall`函数必须具有原型。 此调用约定仅在面向 x86 的编译器中可用，面向其他体系结构的编译器忽略。

**/Gz**指定`__stdcall`除 c + + 成员函数的所有函数的调用约定，函数名为`main`，和标记的函数`__cdecl`， `__fastcall`，或`__vectorcall`。 所有`__stdcall`函数必须具有原型。 此调用约定仅在面向 x86 的编译器中可用，面向其他体系结构的编译器忽略。

**/Gv**指定`__vectorcall`除 c + + 成员函数的所有函数的调用约定，函数名的为主，函数与`vararg`变量自变量列表中或标记有冲突的函数`__cdecl`，`__stdcall`，或`__fastcall`属性。 此调用约定在 x86 和 x64 体系结构支持/arch:sse2 及以上版本才可用，并忽略由面向 ARM 体系结构的编译器。

采用可变数量的参数的函数必须标记为`__cdecl`。

**/Gd**， **/Gr**， **/Gv**并 **/Gz**都不符合[/clr: safe](../../build/reference/clr-common-language-runtime-compilation.md)或 **/clr: pure**. **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

> [!NOTE]
> 默认情况下，对于 x86 处理器，c + + 成员函数使用[__thiscall](../../cpp/thiscall.md)。

适用于所有处理器，显式标记为一个成员函数`__cdecl`， `__fastcall`， `__vectorcall`，或`__stdcall`如果它不会忽略该体系结构上使用指定的调用约定。 始终采用可变数量的参数，则会使用一个成员函数`__cdecl`调用约定。

这些编译器选项对 c + + 方法和函数的名称修饰无效。 除非声明为`extern "C"`，c + + 方法和函数使用不同的名称修饰方案。 有关详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。

有关调用约定的详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

## <a name="cdecl-specifics"></a>__cdecl 细节

在 x86 处理器，所有函数参数都传递到堆栈上从右到左。 在 ARM 和 x64 体系结构中，某些参数通过寄存器进行传递和从右到左，在堆栈上的其余部分传递。 调用的例程中弹出参数在堆栈。

对于 C，`__cdecl`命名的函数名称的约定使用前面带下划线 ( `_` ); 执行没有任何大小写转换。 除非声明为`extern "C"`，c + + 函数使用不同的名称修饰方案。 有关详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。

## <a name="fastcall-specifics"></a>__fastcall 细节

一些`__fastcall`函数的自变量将传入寄存器 (对于 x86 处理器、 ECX 和 EDX)，和其余部分从右到左推送到堆栈上。 被调用的例程在返回之前弹出堆栈从这些自变量。 通常情况下， **/Gr**缩短执行时间。

> [!NOTE]
> 当你使用时要小心`__fastcall`用内联程序集语言编写的任何函数调用约定。 您对寄存器的使用可能与编译器的使用发生冲突。

对于 C，`__fastcall`命名的函数名称的约定使用前面带 at 符号 (**\@**) 后跟函数的参数，以字节为单位的大小。 没有任何大小写转换是完成的。 编译器使用此模板的命名约定：

`@function_name@number`

当你使用`__fastcall`命名约定，使用标准包含文件。 否则，会出现未解析的外部引用。

## <a name="stdcall-specifics"></a>__stdcall 细节

一个`__stdcall`从右到左，函数的参数推送到堆栈和被调用的函数在返回之前弹出堆栈从这些自变量。

对于 C，`__stdcall`命名的函数名称的约定使用前面带下划线 (**\_**) 并后跟 at 符号 (**\@**) 和函数的大小以字节为单位的自变量。 不执行任何大小写转换。 编译器使用此模板的命名约定：

`_functionname@number`

## <a name="vectorcall-specifics"></a>__vectorcall 特定

一个`__vectorcall`函数的整数自变量传递的值，使用最多两个 （在 x86) 或 （在 x64 上） 的四个整数寄存器，，而最多六个 XMM 寄存器的浮点和矢量值和其余部分传递到堆栈上从右到左。 在返回之前被调用的函数清理堆栈。 在 XMM0 中返回向量和浮点返回值。

对于 C，`__vectorcall`命名约定使用函数名称后跟两个 at 符号 (**\@\@**) 和函数的参数，以字节为单位的大小。 不执行任何大小写转换。 编译器使用此模板的命名约定：

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**C/c + +** > **高级**属性页。

1. 修改**调用约定**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>。

## <a name="see-also"></a>请参阅

- [编译器选项](../../build/reference/compiler-options.md)
- [设置编译器选项](../../build/reference/setting-compiler-options.md)

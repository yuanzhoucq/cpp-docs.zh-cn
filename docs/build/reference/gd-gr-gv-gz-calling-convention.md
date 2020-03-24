---
title: /Gd、/Gr、/Gv、/Gz（调用约定）
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
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
ms.openlocfilehash: ab10ac1a4d0c327ff4d0ae54620f3fde752e020b
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150805"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd、/Gr、/Gv、/Gz（调用约定）

这些选项确定函数参数推送到堆栈中的顺序、调用函数或被调用函数是否在调用结束时从堆栈中删除参数，以及编译器用于标识各个函数的名称装饰约定。

## <a name="syntax"></a>语法

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/Gz**

## <a name="remarks"></a>备注

默认设置“/Gd”为除 C++ 成员函数和标记为 [__stdcall](../../cpp/stdcall.md)、[__fastcall](../../cpp/fastcall.md) 或 [__vectorcall](../../cpp/vectorcall.md) 的函数之外的所有函数指定 [__cdecl](../../cpp/cdecl.md) 调用约定。

“/Gr”为除 C++ 成员函数、名为 `main` 的函数以及标记为 `__cdecl`、`__stdcall` 或 `__vectorcall` 的函数之外的所有函数指定 `__fastcall` 调用约定。 所有 `__fastcall` 函数都必须有原型。 此调用约定仅在面向 x86 的编译器中可用，在面向其他体系结构的编译器中被忽略。

“/Gz”为除 C++ 成员函数、名为 `main` 的函数以及标记为 `__cdecl`、`__fastcall` 或 `__vectorcall` 的函数之外的所有函数指定 `__stdcall` 调用约定。 所有 `__stdcall` 函数都必须有原型。 此调用约定仅在面向 x86 的编译器中可用，在面向其他体系结构的编译器中被忽略。

**/Gv**为除成员函数、名为 `main`的C++函数、具有 `vararg` 变量参数列表的函数或标记为冲突的 `__cdecl`、`__stdcall`或 `__fastcall` 特性的函数之外的所有函数指定 `__vectorcall` 调用约定。 此调用约定仅在支持 /arch:SSE2 及更高版本的 x86 和 x64 体系结构上可用，并且被面向 ARM 架构的编译器忽略。

采用可变数量参数的函数必须标记为 `__cdecl`。

/Gd、/Gr、/Gv 和 /Gz 与 [/clr:safe](clr-common-language-runtime-compilation.md) 或 **/clr:pure** 不兼容。 “/clr:pure”和“/clr:safe”编译器选项在 Visual Studio 2015 中已弃用，并且在 Visual Studio 2017 和更高版本中不受支持。

> [!NOTE]
> 默认情况下，对于 x86 处理器，C++ 成员函数使用 [__thiscall](../../cpp/thiscall.md)。

对于所有处理器，显式标记为 `__cdecl`、`__fastcall`、`__vectorcall` 或 `__stdcall` 的成员函数使用指定的调用约定，前提是该函数在此体系结构上不会被忽略。 采用可变数量参数的成员函数始终使用 `__cdecl` 调用约定。

这些编译器选项对 C++ 方法和函数的名称修饰没有影响。 除非声明为 `extern "C"`，否则 C++ 方法和函数使用其他名称修饰方案。 有关详细信息，请参阅[修饰名](decorated-names.md)。

有关调用约定的详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

## <a name="__cdecl-specifics"></a>__cdecl 详细信息

在 x86 处理器上，所有函数参数都从右向左传递到堆栈上。 在 ARM 和 x64 体系结构上，某些参数通过寄存器进行传递，其余参数从右向左传递到堆栈上。 调用例程从堆栈中弹出参数。

对于 C，`__cdecl` 命令约定使用以下划线 ( `_` ) 开头的函数名称；不执行任何大小写转换。 除非声明为 `extern "C"`，否则 C++ 函数使用其他名称修饰方案。 有关详细信息，请参阅[修饰名](decorated-names.md)。

## <a name="__fastcall-specifics"></a>__fastcall 详细信息

`__fastcall` 函数的某些参数在寄存器中传递（针对 x86 处理器、ECX 和 EDX），其余参数从右向左推送到堆栈上。 所调用的例程在返回之前从堆栈中弹出这些参数。 通常情况下，/Gr 可减少执行时间。

> [!NOTE]
> 为采用内联程序集语言编写的任何函数使用 `__fastcall` 调用约定时，请务必小心。 使用寄存器可能与使用编译器产生冲突。

对于 C，`__fastcall` 命名约定使用以 \@ 符号开头、后跟函数参数大小（字节）的函数名称。 不执行任何大小写转换。 编译器将此模板用于命名约定：

`@function_name@number`

使用 `__fastcall` 命名约定时，请使用标准包含文件。 否则，会出现无法解析的外部引用。

## <a name="__stdcall-specifics"></a>__stdcall 详细信息

`__stdcall` 函数的参数从右向左推送到堆栈上，所调用的函数在返回之前从堆栈中弹出这些参数。

对于 C，`__stdcall` 命名约定使用以下划线 (\_) 开头、后跟 \@ 符号和函数参数大小（字节）的函数名称。 不执行任何大小写转换。 编译器将此模板用于命名约定：

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall 详细信息

`__vectorcall` 函数的整数参数按值传递，最多使用两个（x86）或四个（在 x64 上）整数寄存器上，最多六个 XMM 寄存器（对于浮点和向量值）传递，其余部分将从右到左传递到堆栈。 被调用的函数在返回之前清除堆栈。 向量和浮点返回值在 XMM0 中返回。

对于 C，`__vectorcall` 命名约定使用后跟两个 \@\@ 符号和函数参数大小（字节）的函数名称。 不执行任何大小写转换。 编译器将此模板用于命名约定：

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“C/C++” > “高级”属性页。

1. 修改“调用约定”属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>。

## <a name="see-also"></a>请参阅

- [MSVC 编译器选项](compiler-options.md)
- [MSVC 编译器命令行语法](compiler-command-line-syntax.md)

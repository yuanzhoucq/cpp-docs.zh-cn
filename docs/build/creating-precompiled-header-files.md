---
title: 预编译的头文件
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 071839df431071a7d8921d1b445094f886ad38e2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422846"
---
# <a name="precompiled-header-files"></a>预编译的头文件

在 Visual Studio 中创建新项目时，会将名为 *.pch*的*预编译头文件*添加到项目。 （在 Visual Studio 2017 及更早版本中，该文件称为*stdafx.h*。）此文件的目的是加快生成过程。 应在此处包含任何稳定的标头文件（例如 `<vector>`标准库标头）。 预编译标头仅在修改了它或它包含的任何文件时进行了编译。 如果只在项目源代码中进行更改，则生成将跳过预编译标头的编译。 

预编译标头的编译器选项为[/y](reference/y-precompiled-headers.md)。 在项目属性页中，选项位于 "**配置属性" 下 > "CC++ /> 预编译标头**"。 您可以选择不使用预编译标头，也可以指定头文件名称以及输出文件的名称和路径。 

## <a name="custom-precompiled-code"></a>自定义预编译代码

对于需要很长时间生成的大型项目，可能需要考虑创建自定义预编译文件。 Microsoft C 和 C++ 编译器提供预编译任何 C 或 C++ 代码（包括内联代码）的选项。 使用此性能功能，可以编译稳定的代码正文，在文件中存储已编译的代码状态，并在后续编译过程中将预编译代码和仍在开发的代码合并在一起。 每个后续编译的速度都更快，因为无需重新编译稳定的代码。

## <a name="when-to-precompile-source-code"></a>何时预编译源代码

在开发周期中，预编译代码非常有用，可缩短编译时间，尤其是在以下情况下：

- 始终使用大量更改的代码。

- 程序包含多个模块，所有模块都使用一组标准的包含文件和相同的编译选项。 在这种情况下，所有包含文件都可以预编译为一个预编译标头。

第一次编译（创建预编译头（PCH）文件）所花的时间比后续编译要长一些。 后续编译可以通过包含预编译代码更快地进行。

可以预编译 C 和C++程序。 在C++编程中，常见的做法是将类接口信息分隔到头文件中。 以后可以在使用类的程序中包含这些头文件。 通过预编译这些标头，可以减少程序编译所用的时间。

> [!NOTE]
> 虽然每个源文件只能使用一个预编译标头（.pch）文件，但你可以在一个项目中使用多个 .pch 文件。

## <a name="two-choices-for-precompiling-code"></a>预编译代码的两种方法

可以预编译任何 C 或C++代码;你不仅限于预编译头文件。

预编译需要计划，但如果预编译的源代码不是简单的头文件，则可以更快地进行编译。

当您知道您的源文件使用一组常用的标头文件，但不按相同顺序包含它们，或者您想要在预编译中包含源代码时，预编译代码。

预编译标头选项为[/yc （创建预编译标头文件）](reference/yc-create-precompiled-header-file.md)和[/Yu （使用预编译标头文件）](reference/yu-use-precompiled-header-file.md)。 使用 **/yc**创建预编译标头。 与可选的[hdrstop](../preprocessor/hdrstop.md)杂注一起使用时， **/yc**允许预编译头文件和源代码。 选择 **/yu**以在现有编译中使用现有预编译头。 你还可以将 **/fp**与 **/yc**和 **/yu**选项一起使用，为预编译标头提供备用名称。

用于 **/yu**和 **/yc**的编译器选项参考主题介绍了如何在开发环境中访问此功能。

## <a name="precompiled-header-consistency-rules"></a>预编译标头一致性规则

由于 PCH 文件包含有关计算机环境的信息以及有关程序的内存地址信息，因此只应在创建该文件的计算机上使用 PCH 文件。

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>按文件使用预编译头的一致性规则

[/Yu](reference/yu-use-precompiled-header-file.md)编译器选项允许你指定要使用的 PCH 文件。

当使用 PCH 文件时，编译器会假设相同的编译环境（使用一致的编译器选项、杂注等）在创建 PCH 文件时生效，除非您另行指定。 如果编译器检测到不一致，则会发出警告，并在可能的情况下标识不一致。 此类警告不一定表示 PCH 文件有问题;它们只是警告您可能出现的冲突。 以下各节介绍了 PCH 文件的一致性要求。

### <a name="compiler-option-consistency"></a>编译器选项一致性

使用 PCH 文件时，以下编译器选项可能触发不一致性警告：

- 使用预处理器（/D）选项创建的宏在创建 PCH 文件的编译和当前编译之间必须相同。 不检查已定义常量的状态，但如果发生这些更改，则可能会发生不可预知的结果。

- PCH 文件不适用于/E 和/EP 选项。

- PCH 文件必须使用生成浏览信息（/FR）选项或 "排除本地变量" （/Fr）选项创建，然后使用 PCH 文件的后续编译才能使用这些选项。

### <a name="c-70-compatible-z7"></a>C 7.0-兼容（/Z7）

如果创建 PCH 文件后此选项生效，则使用 PCH 文件的后续编译可以使用调试信息。

如果在创建 PCH 文件时 C 7.0 兼容（/Z7）选项不起作用，则使用 PCH 文件和/Z7 的后续编译将触发警告。 调试信息放在当前 .obj 文件中，并且在 PCH 文件中定义的本地符号不适用于调试器。

### <a name="include-path-consistency"></a>包含路径一致性

PCH 文件不包含有关在创建时生效的包含路径的信息。 当使用 PCH 文件时，编译器始终使用在当前编译中指定的包含路径。

### <a name="source-file-consistency"></a>源文件一致性

当你指定 "使用预编译头文件（/Yu）" 选项时，编译器将忽略出现在将预编译的源代码中的所有预处理器指令（包括杂注）。 此类预处理器指令指定的编译必须与用于创建预编译标头文件（/Yc）选项的编译相同。

### <a name="pragma-consistency"></a>Pragma 一致性

在 PCH 文件创建期间处理的杂注通常会影响随后使用 PCH 文件时使用的文件。 `comment` 和 `message` 杂注不会影响编译的其余部分。

这些杂注只影响 PCH 文件中的代码;它们不会影响随后使用 PCH 文件的代码：

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

这些杂注作为预编译标头的一部分保留，并影响使用预编译标头的编译的其余部分：

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>/Yc 和 /Yu 的一致性规则

当使用使用/Yc 或/Yu 创建的预编译标头时，编译器会将当前编译环境与创建 PCH 文件时存在的编译环境进行比较。 请确保指定与上一个环境一致的环境（使用一致的编译器选项、杂注等）进行当前编译。 如果编译器检测到不一致，则会发出警告，并在可能的情况下标识不一致。 此类警告不一定表示 PCH 文件有问题;它们只是警告您可能出现的冲突。 以下各节介绍预编译头的一致性要求。

### <a name="compiler-option-consistency"></a>编译器选项一致性

此表列出了在使用预编译头时可能触发不一致性警告的编译器选项：

|选项|名称|规则|
|------------|----------|----------|
|/D|定义常数和宏|在创建预编译标头的编译和当前编译之间必须相同。 不检查已定义常量的状态，但如果您的文件依赖于更改的常量的值，则可能会出现不可预知的结果。|
|/E 或/EP|将预处理器输出复制到标准输出|预编译标头不适用于/E 或/EP 选项。|
|/Fr 或/FR|生成 Microsoft 源浏览器信息|为了使/Fr 和/FR 选项与/Yu 选项一起使用，在创建预编译标头时，它们也必须已生效。 使用预编译标头的后续编译还会生成源浏览器信息。 浏览器信息放置在单个 .sbr 文件中，由其他文件引用，其方式与 CodeView 信息相同。 不能重写源浏览器信息的位置。|
|/GA、/GD、/GE、/Gw 或/GW|Windows 协议选项|在创建预编译标头的编译和当前编译之间必须相同。 如果这些选项不同，则会出现一条警告消息。|
|/ZI|生成完整的调试信息|如果创建预编译标头时此选项生效，则使用预编译的后续编译可以使用该调试信息。 如果在创建预编译标头时/Zi 不起作用，则使用预编译和/Zi 选项的后续编译将触发警告。 调试信息放在当前的对象文件中，并且在预编译头中定义的本地符号不适用于调试器。|

> [!NOTE]
>  预编译标头功能仅适用于 C 和C++源文件。

## <a name="using-precompiled-headers-in-a-project"></a>在项目中使用预编译头

前面几节提供预编译标头概述：/Yc 和/Yu、/Fp 选项和[hdrstop](../preprocessor/hdrstop.md)杂注。 本节介绍在项目中使用手动预编译标头选项的方法;它以示例生成文件和它管理的代码结尾。

对于在项目中使用手动预编译标头选项的另一种方法，请在 Visual Studio 的默认安装过程中，学习在 MFC\SRC 目录中创建的一个生成程序。 这些生成程序对此部分中提供的方法采用类似的方法，但更充分地利用 Microsoft 程序维护实用工具（NMAKE）宏，并提供对生成过程的更多控制。

## <a name="pch-files-in-the-build-process"></a>生成过程中的 PCH 文件

软件项目的基本代码通常包含在多个 C 或C++源文件、对象文件、库和头文件中。 通常，生成文件会将这些元素合并到可执行文件中。 下图显示了使用预编译头文件的生成文件的结构。 此关系图中的 NMAKE 宏名称和文件名与在[pch 的示例生成文件](#sample-makefile-for-pch)和[Pch 的示例代码](#example-code-for-pch)中找到的示例代码中的名称相同。

该图使用三个关系图设备来显示生成过程的流。 命名矩形表示每个文件或宏;这三个宏表示一个或多个文件。 灰色区域表示每个编译或链接操作。 箭头显示编译或链接过程中合并了哪些文件和宏。

![使用预编译头文件的生成文件的结构](media/vc30ow1.gif "使用预编译头文件的生成文件的结构") <br/>
使用预编译标头文件的生成文件结构

从关系图的顶部开始，STABLEHDRS 和 BOUNDRY 都是 NMAKE 宏，其中列出了不可能需要重新编译的文件。 这些文件由命令字符串编译

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

仅当预编译头文件（稳定 .pch）不存在时，或者在对两个宏中列出的文件进行更改时。 在这两种情况下，预编译标头文件仅包含 STABLEHDRS 宏列出的文件中的代码。 列出要在 BOUNDRY 宏中预编译的最后一个文件。

在这些宏中列出的文件可以是头文件，也可以是 C C++或源文件。 （单个 PCH 文件不能与 C 和C++模块一起使用。）请注意，可以使用**hdrstop**宏在 BOUNDRY 文件中的某个时间点停止预编译。 有关详细信息，请参阅[hdrstop](../preprocessor/hdrstop.md) 。

继续下图，APPLIB 表示最终应用程序中使用的支持代码。 它从 APPLIB、UNSTABLEHDRS 宏中列出的文件以及预编译标头中的预编译代码创建。

MYAPP 表示最终的应用程序。 它从 MYAPP、UNSTABLEHDRS 宏中列出的文件和预编译标头中的预编译代码创建。

最后，可执行文件（MYAPP。EXE）是通过链接 OBJ 宏（APPLIB 和 MYAPP）中列出的文件创建的。

## <a name="sample-makefile-for-pch"></a>PCH 的示例生成文件

以下生成文件使用宏和！如果、！否则，！ENDIF 控制流命令结构，简化对项目的适应。

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

除了 STABLEHDRS、BOUNDRY 和 UNSTABLEHDRS 宏，如在[生成过程中的 PCH 文件](#pch-files-in-the-build-process)中的 "使用预编译头文件的生成文件的结构" 中所示的和宏，此生成文件提供了 CLFLAGS 宏和 LINKFLAGS 宏。 您必须使用这些宏来列出编译器和链接器选项，这些选项适用于是否生成应用程序的可执行文件的调试或最终版本。 还有一个库宏，你可以在其中列出你的项目所需的库。

Makefile 还使用！如果、！否则，！ENDIF 检测是否在 NMAKE 命令行上定义调试符号：

```NMAKE
NMAKE DEBUG=[1|0]
```

此功能使您可以在开发过程中和程序的最终版本中使用相同的生成程序-对最终版本使用 DEBUG = 0。 以下命令行是等效的：

```NMAKE
NMAKE
NMAKE DEBUG=0
```

有关生成程序的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)。 另请参阅[MSVC 编译器选项](reference/compiler-options.md)和[MSVC 链接器选项](reference/linker-options.md)。

## <a name="example-code-for-pch"></a>PCH 的示例代码

以下源文件用于[生成过程中的 Pch 文件](#pch-files-in-the-build-process)和[Pch 的示例生成](#sample-makefile-for-pch)文件中所述的生成文件。 请注意，注释包含重要的信息。

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
using namespace std;
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>另请参阅

[C/C++ 生成参考](reference/c-cpp-building-reference.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)

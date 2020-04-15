---
title: 预编译的头文件
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 158301ec3caacced1663892071b17ef2b8f8e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328673"
---
# <a name="precompiled-header-files"></a>预编译的头文件

在 Visual Studio 中创建新项目时，将添加名为*pch.h* *的预编译标头文件*。 （在 Visual Studio 2017 和更早版本中，该文件称为*stdafx.h*.）该文件的目的是加快生成过程。 任何稳定的标头文件（例如标准库标头（如`<vector>`）都应在此处包含。 仅当预编译标头或其包含的任何文件被修改时，才会编译它。 如果仅在项目源代码中进行更改，则生成将跳过预编译标头的编译。

预编译标头的编译器选项为[/Y](reference/y-precompiled-headers.md)。 在项目属性页中，选项位于**配置属性> C/C++>预编译标头**。 您可以选择不使用预编译的标头，也可以指定标头文件名以及输出文件的名称和路径。

## <a name="custom-precompiled-code"></a>自定义预编译代码

对于需要大量时间构建的大型项目，您可能需要考虑创建自定义预编译文件。 Microsoft C 和 C++ 编译器提供预编译任何 C 或 C++ 代码（包括内联代码）的选项。 使用此性能功能，可以编译稳定的代码正文，在文件中存储已编译的代码状态，并在后续编译过程中将预编译代码和仍在开发的代码合并在一起。 每个后续编译的速度都更快，因为无需重新编译稳定的代码。

## <a name="when-to-precompile-source-code"></a>何时预编译源代码

预编译代码在开发周期中非常有用，用于缩短编译时间，尤其是在以下情况：

- 您始终使用不常更改的大量代码。

- 您的程序包含多个模块，所有这些模块都使用一组标准的包含文件和相同的编译选项。 在这种情况下，所有包含文件都可以预编译为一个预编译标头。

第一个编译（创建预编译标头 （PCH） 文件）比后续编译长一点。 通过包括预编译的代码，后续编译可以更快地进行。

您可以预编译 C 和C++程序。 在C++编程中，通常的做法是将类接口信息分离到头文件中。 这些标头文件以后可以包含在使用 类的程序中。 通过预编译这些标头，可以减少程序编译所需的时间。

> [!NOTE]
> 尽管每个源文件只能使用一个预编译的标头 （.pch） 文件，但可以在项目中使用多个 .pch 文件。

## <a name="two-choices-for-precompiling-code"></a>预编译代码的两种方法

您可以预编译任何 C 或C++代码;您不限于仅预编译标头文件。

预编译需要规划，但如果预编译简单标头文件以外的源代码，则预编译速度会明显加快。

当您知道源文件使用常用的标头文件集，但不按相同的顺序包括它们，或者当您希望在预编译中包括源代码时，请预编译代码。

预编译标头选项为[/Yc（创建预编译的标头文件）](reference/yc-create-precompiled-header-file.md)和[/Yu（使用预编译的标头文件）。](reference/yu-use-precompiled-header-file.md) 使用 **/Yc**创建预编译标头。 当与可选的[hdrstop](../preprocessor/hdrstop.md)实用素一起使用时 **，/Yc**允许您预编译标头文件和源代码。 选择 **/Yu**以在现有编译中使用现有的预编译标头。 您还可以使用 **/Fp**与 **/Yc**和 **/Yu**选项一起为预编译标头提供替代名称。

**/Yu**和 **/Yc**的编译器选项参考主题讨论如何在开发环境中访问此功能。

## <a name="precompiled-header-consistency-rules"></a>预编译标头一致性规则

由于 PCH 文件包含有关计算机环境的信息以及有关该程序的内存地址信息，因此应仅在创建该程序的计算机上使用 PCH 文件。

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>按文件使用预编译头的一致性规则

[/Yu](reference/yu-use-precompiled-header-file.md)编译器选项允许您指定要使用的 PCH 文件。

使用 PCH 文件时，编译器将假定在创建 PCH 文件时有效的编译环境（使用一致的编译器选项、杂注等）有效，除非您另有说明。 如果编译器检测到不一致，它会发出警告，并尽可能识别不一致。 此类警告不一定表示 PCH 文件有问题;因此，这些警告并不一定表示 PCH 文件存在问题。他们只是警告你潜在的冲突。 PCH文件的一致性要求如下所述。

### <a name="compiler-option-consistency"></a>编译器选项一致性

使用 PCH 文件时，以下编译器选项可能会触发不一致警告：

- 使用预处理器 （/D） 选项创建的宏在创建 PCH 文件和当前编译的编译之间必须相同。 未检查已定义的常量的状态，但如果更改这些常量，则可能会出现不可预知的结果。

- PCH 文件不适用于 /E 和 /EP 选项。

- 在使用 PCH 文件的后续编译可以使用这些选项之前，必须使用生成浏览信息 （/FR） 选项或排除局部变量 （/Fr） 选项创建 PCH 文件。

### <a name="c-70-compatible-z7"></a>C 7.0 兼容 （/Z7）

如果此选项在创建 PCH 文件时有效，则使用 PCH 文件的后续编译可以使用调试信息。

如果在创建 PCH 文件时 C 7.0 兼容 （/Z7） 选项无效，则使用 PCH 文件和 /Z7 的后续编译将触发警告。 调试信息放置在当前 .obj 文件中，并且在 PCH 文件中定义的本地符号对调试器不可用。

### <a name="include-path-consistency"></a>包括路径一致性

PCH 文件不包含有关创建时有效的包含路径的信息。 使用 PCH 文件时，编译器始终使用当前编译中指定的包含路径。

### <a name="source-file-consistency"></a>源文件一致性

指定"使用预编译标头文件 （/Yu）"选项时，编译器将忽略将预编译的源代码中显示的所有预处理器指令（包括杂注）。 此类预处理器指令指定的编译必须与创建预编译标头文件 （/Yc） 选项的编译相同。

### <a name="pragma-consistency"></a>实用一致性

在创建 PCH 文件期间处理的实用主义通常会影响随后使用 PCH 文件的文件。 和`comment``message`杂注不会影响编译的其余部分。

这些杂注仅影响 PCH 文件中的代码;它们不会影响随后使用 PCH 文件的代码：

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

使用使用 /Yc 或 /Yu 创建的预编译标头时，编译器会将当前编译环境与创建 PCH 文件时存在的编译环境进行比较。 请确保为当前编译指定与前一个环境一致的环境（使用一致的编译器选项、杂注等）。 如果编译器检测到不一致，它会发出警告，并尽可能识别不一致。 此类警告不一定表示 PCH 文件有问题;因此，这些警告并不一定表示 PCH 文件存在问题。他们只是警告你潜在的冲突。 以下各节解释预编译标头的一致性要求。

### <a name="compiler-option-consistency"></a>编译器选项一致性

此表列出了在使用预编译标头时可能引发不一致警告的编译器选项：

|选项|名称|规则|
|------------|----------|----------|
|/D|定义常量和宏|创建预编译标头的编译和当前编译之间必须相同。 未检查已定义的常量的状态，但如果文件依赖于更改的常量的值，则可能会出现不可预知的结果。|
|/E 或 /EP|将预处理器输出复制到标准输出|预编译标头不适用于 /E 或 /EP 选项。|
|/Fr 或 /FR|生成微软源浏览器信息|对于 /Fr 和 /FR 选项在 /Yu 选项中有效，它们也必须在创建预编译标头时有效。 使用预编译标头的后续编译也会生成源浏览器信息。 浏览器信息放置在单个 .sbr 文件中，其他文件以与 CodeView 信息相同的方式引用这些信息。 您不能覆盖源浏览器信息的位置。|
|/GA、/GD、/GE、/Gw 或 /GW|Windows 协议选项|创建预编译标头的编译和当前编译之间必须相同。 如果这些选项不同，则会生成警告消息。|
|/Zi|生成完整的调试信息|如果此选项在创建预编译标头时有效，则使用预编译的后续编译可以使用该调试信息。 如果在创建预编译标头时 /Zi 无效，则使用预编译和 /Zi 选项的后续编译将触发警告。 调试信息放置在当前对象文件中，并且在预编译标头中定义的本地符号对调试器不可用。|

> [!NOTE]
> 预编译标头工具仅用于 C 和 C++源文件。

## <a name="using-precompiled-headers-in-a-project"></a>在项目中使用预编译头

前面的各节概述了预编译标头：/Yc 和 /Yu、/Fp 选项和[hdrstop](../preprocessor/hdrstop.md)杂注。 本节介绍在项目中使用手动预编译标头选项的方法;它以一个示例 makefile 及其管理的代码结束。

对于在项目中使用手动预编译标头选项的另一种方法，请研究在 Visual Studio 的默认设置期间创建的 MFC_SRC 目录中的一个 makefile。 这些 makefile 采用与本节中介绍的方法类似的方法，但更多地利用了 Microsoft 程序维护实用程序 （NMAKE） 宏，并更好地控制了生成过程。

## <a name="pch-files-in-the-build-process"></a>生成过程中的 PCH 文件

软件项目的代码库通常包含在多个 C 或C++源文件、对象文件、库和标头文件中。 通常，makefile 将这些元素组合为可执行文件。 下图显示了使用预编译标头文件的 makefile 的结构。 此关系图中的 NMAKE 宏名和文件名与[PCH 示例 Makefile](#sample-makefile-for-pch)和[PCH 示例代码](#example-code-for-pch)中的示例代码中的那些名称一致。

该图使用三个图表设备来显示生成过程的流。 命名矩形表示每个文件或宏;三个宏表示一个或多个文件。 已对区域表示每个编译或链接操作。 箭头显示在编译或链接过程中组合的文件和宏。

![使用预编译标头文件的 makefile 的结构](media/vc30ow1.gif "使用预编译标头文件的 makefile 的结构") <br/>
使用预编译标头文件的生成文件结构

从关系图的顶部开始，STABLEHDRS 和 BOUNDRY 都是 NMAKE 宏，其中列出了不需要重新编译的文件。 这些文件由命令字符串编译

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

仅当预编译的标头文件 （STABLE.pch） 不存在或对两个宏中列出的文件进行更改时。 在这两种情况下，预编译的标头文件将仅包含来自 STABLEHDRS 宏中列出的文件的代码。 列出要在 BOUNDRY 宏中预编译的最后一个文件。

在这些宏中列出的文件可以是头文件或 C 或C++源文件。 （单个 PCH 文件不能同时用于 C 和 C++ 模块。请注意，您可以使用**hdrstop**宏在 BOUNDRY 文件中的某个点停止预编译。 有关详细信息，请参阅[hdrstop。](../preprocessor/hdrstop.md)

APPLIB.obj 继续向下表示最终应用程序中使用的支持代码。 它创建自 APPLIB.cpp，UNSTABLEHDRS 宏中列出的文件，并从预编译标头中预编译代码。

MYAPP.obj 代表您的最终申请。 它创建于 MYAPP.cpp，即 UNSTABLEHDRS 宏中列出的文件，并从预编译标头中预编译代码。

最后，可执行文件（MYAPP）。EXE）是通过链接 OBJS 宏（APPLIB.obj 和 MYAPP.obj）中列出的文件创建的。

## <a name="sample-makefile-for-pch"></a>PCH 的示例生成文件

以下 makefile 使用宏和 ！如果！还！ENDIF 控制流命令结构，以简化其对项目的适应。

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

除了[生成过程中 PCH 文件中](#pch-files-in-the-build-process)的"使用预编译的标头文件的 Makefile 的结构"中所示的 STABLEHDRS、BOUNDRY 和 UNSTABLEHDRS 宏外，此 makefile 提供了 CLFLAGS 宏和 LINKFLAGS 宏。 您必须使用这些宏来列出编译器和链接器选项，这些选项适用于生成应用程序的可执行文件的调试版本还是最终版本。 还有一个 LIBS 宏，您可以在其中列出项目所需的库。

makefile 也使用 ！如果！还！ENDIF 用于检测您是否在 NMAKE 命令行上定义 DEBUG 符号：

```NMAKE
NMAKE DEBUG=[1|0]
```

此功能使您能够在开发和程序的最终版本中使用相同的 makefile - 将 DEBUG_0 用于最终版本。 以下命令行等效：

```NMAKE
NMAKE
NMAKE DEBUG=0
```

有关制作文件的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)。 另请参阅[MSVC 编译器选项](reference/compiler-options.md)和[MSVC 链接器选项](reference/linker-options.md)。

## <a name="example-code-for-pch"></a>PCH 的示例代码

以下源文件用于[生成过程中 PCH 文件中](#pch-files-in-the-build-process)描述的 makefile 和[PCH 的"示例使文件](#sample-makefile-for-pch)"。 请注意，注释包含重要信息。

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

---
title: 创建预编译标头文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pch
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e050532de79a82291948862840b4c8fa6a3b4995
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703191"
---
# <a name="creating-precompiled-header-files"></a>创建预编译标头文件

Microsoft C 和 C++ 编译器提供预编译任何 C 或 C++ 代码（包括内联代码）的选项。 使用此性能功能，可以编译稳定的代码正文，在文件中存储已编译的代码状态，并在后续编译过程中将预编译代码和仍在开发的代码合并在一起。 每个后续编译的速度都更快，因为无需重新编译稳定的代码。

本主题涵盖以下预编译标头内容：

- [何时预编译源代码](#when-to-precompile-source-code)

- [预编译代码的两种方法](#two-choices-for-precompiling-code)

- [预编译标头一致性规则](#precompiled-header-consistency-rules)

- [按文件使用预编译标头的一致性规则](#consistency-rules-for-per-file-use-of-precompiled-headers)

- [/Yc 和 /Yu 的一致性规则](#consistency-rules-for-yc-and-yu)

- [在项目中使用预编译标头](#using-precompiled-headers-in-a-project)

- [生成过程中的 PCH 文件](#pch-files-in-the-build-process)

- [PCH 的示例生成文件](#sample-makefile-for-pch)

- [PCH 的示例代码](#example-code-for-pch)

预编译标头与相关的编译器选项的参考信息，请参阅[/Y （预编译标头）](../../build/reference/y-precompiled-headers.md)。

<a name="when-to-precompile-source-code"></a>

## <a name="when-to-precompile-source-code"></a>何时预编译源代码

预编译的代码可在开发周期中减少编译时间，尤其是：

- 始终使用大量的更改不频繁的代码。

- 您的程序包含多个模块，所有这些使用一组标准的包含文件和相同的编译选项。 在这种情况下，所有包含文件可以预编译为一个预编译标头。

首次编译 — 与创建预编译标头 (PCH) 文件，采用更长时间比后续编译。 通过包括预编译的代码，后续编译可以更快地继续。

您可以预编译 C 和 c + + 程序。 在 c + + 编程，它是常见的做法单独的头文件的类接口信息。 更高版本可以使用类的程序中包含这些标头文件。 通过预编译这些标头，可以减少程序编译所花费的时间。

> [!NOTE]
>  虽然每个源代码文件，可以使用一个预编译标头 (.pch) 文件，可以使用在项目中的多个.pch 文件。

<a name="two-choices-for-precompiling-code"></a>

# <a name="two-choices-for-precompiling-code"></a>预编译代码的两种方法

使用 Visual c + +，您可以预编译任何 C 或 c + + 代码;并不局限于预编译仅标头文件。

预编译需要进行规划，但它提供明显更快的编译，如果预编译简单标头文件以外的源代码。

当您知道源文件使用一组通用的标头文件，但不将其包含在相同的顺序，或想要包括在预编译的源代码时，预编译代码。

预编译标头选项[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)并[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)。 使用 **/Yc**创建的预编译标头。 当使用具有可选[hdrstop](../../preprocessor/hdrstop.md)杂注， **/Yc** ，可以预编译这两个标头文件和源代码。 选择 **/Yu**在现有的编译中使用现有的预编译标头。 此外可以使用 **/Fp**与 **/Yc**并 **/Yu**选项，以便提供预编译标头的替代名称。

编译器选项引用主题 **/Yu**并 **/Yc**讨论如何访问此功能的开发环境。

<a name="precompiled-header-consistency-rules"></a>

## <a name="precompiled-header-consistency-rules"></a>预编译标头一致性规则

由于 PCH 文件包含有关计算机环境的信息以及有关程序的内存地址信息，应仅使用创建它时所在的计算机上的 PCH 文件。

<a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>按文件使用预编译标头的一致性规则

[/Yu](../../build/reference/yu-use-precompiled-header-file.md)编译器选项可以指定要使用哪个 PCH 文件。

当使用 PCH 文件时，编译器将假定相同的编译环境，另一个使用一致的编译器选项、 杂注，等等 — 那就是实际上创建 PCH 文件，除非另行指定。 如果编译器检测到不一致，它会发出警告，并标识不一致，在可能的情况。 此类警告不一定表示出现问题的 PCH 文件;它们只是警告您可能出现的冲突。 以下各节所述的 PCH 文件的一致性要求。

### <a name="compiler-option-consistency"></a>编译器选项一致性

使用 PCH 文件时，以下编译器选项可触发不一致性警告：

- 创建使用预处理器宏 (/ D) 选项必须为相同之间创建 PCH 文件的编译和当前的编译。 未选中状态的定义的常数，但如果这些更改，则会出现不可预知的结果。

- PCH 文件无法正常使用 /E 和 /EP 选项。

- 必须使用任一生成浏览信息创建 PCH 文件 (/ FR) 选项或排除的本地变量 (/ Fr) 选项后面的编译使用 PCH 文件才能使用这些选项。

### <a name="c-70-compatible-z7"></a>C 7.0 兼容 (/ Z7)

如果此选项有效创建 PCH 文件时，使用 PCH 文件的后续编译可以使用调试信息。

如果 C 7.0 兼容 (/ Z7) 选项是无效的创建 PCH 文件时，使用 PCH 文件和/z7 标识的后续编译触发一条警告。 调试信息放在当前的.obj 文件中，且 PCH 文件中定义的本地符号不支持到调试器。

### <a name="include-path-consistency"></a>包括路径一致性

PCH 文件不包含有关已起作用时创建的包含路径信息。 当使用 PCH 文件时，编译器将始终使用当前编译中指定的 include 路径。

### <a name="source-file-consistency"></a>源文件一致性

在指定使用预编译标头文件 (/Yu) 选项，编译器将忽略所有将预编译的源代码中显示的预处理器指令 （包括杂注）。 由这些预处理器指令指定的编译必须与用于创建预编译的头文件 (/Yc) 选项编译相同。

### <a name="pragma-consistency"></a>杂注一致性

PCH 文件创建的过程通常处理的杂注会影响同随后使用 PCH 文件的文件。 `comment`和`message`杂注不会影响编译的其余部分。

这些杂注会影响仅 PCH 文件; 中的代码它们不会影响随后使用 PCH 文件的代码：

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

这些杂注作为预编译标头的一部分保留，并且会影响使用预编译标头的编译的其余部分：

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

<a name="consistency-rules-for-yc-and-yu"></a>

## <a name="consistency-rules-for-yc-and-yu"></a>/Yc 和 /Yu 的一致性规则

使用 /Yc 或 /Yu 创建预编译标头使用时，编译器将创建 PCH 文件时存在一个当前编译环境进行比较。 请确保指定与上一个 （使用一致的编译器选项、 杂注，等等） 的当前编译一致的环境。 如果编译器检测到不一致，它会发出警告，并标识不一致，在可能的情况。 此类警告不一定表示存在问题的 PCH 文件;它们只是警告您可能出现的冲突。 以下部分介绍预编译标头的一致性要求。

### <a name="compiler-option-consistency"></a>编译器选项一致性

此表列出了使用预编译标头时，可能会触发不一致性警告的编译器选项：

|选项|name|规则|
|------------|----------|----------|
|/D|定义常量和宏|必须创建预编译标头的编译和当前编译之间相同。 未选中状态的定义的常数，但如果你的文件依赖于已更改的常量的值，则会出现不可预知的结果。|
|/E 或 /EP|将预处理器输出复制到标准输出|预编译标头带有 /E 或 /EP 选项无效。|
|/Fr 或 /FR|生成 Microsoft 源浏览器信息|/Fr 和 /FR 选项可与 /Yu 选项一起使用，为在创建预编译标头时它们还必须已生效。 使用预编译标头的后续编译还生成源浏览器信息。 浏览器信息放置在单个.sbr 文件和中的 CodeView 信息与相同的方式引用的其他文件。 不能重写源浏览器信息的位置。|
|/ GA、 /GD、 /GE、 /Gw 或 /GW|Windows 协议选项|必须创建预编译标头的编译和当前编译之间相同。 如果这些选项不同，会导致一条警告消息。|
|/ZI|生成完整的调试信息|如果此选项有效创建预编译标头时，使用预编译的后续编译可以使用该调试信息。 如果 /Zi 不是有效创建预编译标头时，使用预编译和 /Zi 选项的后续编译触发警告。 调试信息放在当前的对象文件中，并预编译标头中定义的本地符号不可用到调试器。|

> [!NOTE]
>  预编译标头功能用于仅在 C 和 c + + 源代码文件中。

<a name="using-precompiled-headers-in-a-project"></a>

## <a name="using-precompiled-headers-in-a-project"></a>在项目中使用预编译标头

前面几节将概括介绍预编译标头： /Yc 和 /Yu，/Fp 选项，并[hdrstop](../../preprocessor/hdrstop.md)杂注。 本部分介绍的项目; 使用手动预编译标头选项的方法它结尾的示例生成文件和它所管理的代码。

在项目中使用手动预编译标头选项的另一个方法，研究 Visual c + + 的默认安装过程中创建 MFC\SRC 目录中的生成文件之一。 这些生成文件采用的本部分中介绍的一个类似方法，但更多地利用 Microsoft 程序维护实用工具 (NMAKE) 宏并提供更好地控制生成过程。

<a name="pch-files-in-the-build-process"></a>

## <a name="pch-files-in-the-build-process"></a>生成过程中的 PCH 文件

软件项目的基本代码通常包含在多个 C 或 c + + 源代码文件、 对象文件、 库和标头文件。 通常情况下，生成文件协调这些元素组合到可执行文件。 下图显示了使用预编译标头文件的生成文件结构。 NMAKE 宏名称和此关系图中的文件名称是与中的示例代码中的一致[PCH 的示例生成文件](#sample-makefile-for-pch)并[PCH 的示例代码](#example-code-for-pch)。

图使用三个关系图的设备来显示生成过程的流。 名为矩形表示，每个文件或宏;三个宏表示一个或多个文件。 阴影的区域表示每个编译或链接的操作。 箭头显示编译或链接过程期间合并的文件和宏。

![使用预编译的头文件的生成](../../build/reference/media/vc30ow1.gif "使用预编译标头文件的生成文件结构")
##### <a name="structure-of-a-makefile-that-uses-a-precompiled-header-file"></a>使用预编译标头文件的生成文件结构

从关系图的顶部，STABLEHDRS 和边界是 NMAKE 宏在其中列出不太可能需要重新编译的文件。 这些文件编译的命令字符串

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

仅当预编译标头文件 （编译） 不存在或对两个宏中列出的文件进行更改。 在任一情况下，预编译的头文件将包含仅从列入 STABLEHDRS 宏的文件的代码。 列出所需边界宏在预编译的最后一个文件。

列表中这些宏的文件可以是标头文件或 C 或 c + + 源文件。 （单个的 PCH 文件不能用于 C 和 c + + 模块。）请注意，可以使用**hdrstop**宏，以停止在某个时间点边界文件中的预编译。 请参阅[hdrstop](../../preprocessor/hdrstop.md)有关详细信息。

APPLIB.obj 继续向下移动关系图，表示在最终应用程序中使用的支持代码。 创建从 APPLIB.cpp，文件列入 UNSTABLEHDRS 宏和预编译预编译标头中的代码。

MYAPP.obj 代表最终应用程序。 创建从 MYAPP.cpp，文件列入 UNSTABLEHDRS 宏和预编译预编译标头中的代码。

最后，可执行文件 (MYAPP。通过链接 OBJ 宏 （APPLIB.obj 和 MYAPP.obj） 中列出的文件创建 EXE)。

<a name="sample-makefile-for-pch"></a>

## <a name="sample-makefile-for-pch"></a>PCH 的示例生成文件

以下生成文件使用宏和 ！如果 ！其他 ！ENDIF 流控制命令结构，以简化其适应功能到你的项目。

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
LINKFLAGS = /NOD /ONERROR:NOEXE
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f
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

除了在图中"结构的生成文件，使用预编译标头文件"中所示的 STABLEHDRS、 边界和 UNSTABLEHDRS 宏[生成过程中的 PCH 文件](#pch-files-in-the-build-process)，此生成文件提供 CLFLAGS 宏和 LINKFLAGS宏。 必须使用这些宏来列出了编译器和链接器选项，以应用是否生成调试版本还是应用程序的可执行文件的最终版本。 此外，还有 LIBS 宏在其中列出库需要你的项目。

生成文件还使用了 ！如果 ！其他 ！ENDIF 来检测是否定义 DEBUG 符号 NMAKE 命令行上：

```NMAKE
NMAKE DEBUG=[1|0]
```

此功能使您可以在开发过程中使用相同的生成文件和程序的最终版本 — 使用调试 = 0 的最终版本。 以下命令行是等效的：

```NMAKE
NMAKE
NMAKE DEBUG=0
```

生成文件的详细信息，请参阅[NMAKE 参考](../../build/nmake-reference.md)。 另请参阅[编译器选项](../../build/reference/compiler-options.md)并[链接器选项](../../build/reference/linker-options.md)。

<a name="example-code-for-pch"></a>

## <a name="example-code-for-pch"></a>PCH 的示例代码

中所述的生成文件中使用以下源文件[生成过程中的 PCH 文件](#pch-files-in-the-build-process)并[PCH 的示例生成文件](#sample-makefile-for-pch)。 请注意，注释包含重要信息。

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
#include<iostream.h>
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

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)
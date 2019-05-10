---
title: 错误 C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: 522bc4a36be59d4e2c9425e50b1238eb9f4aba61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368053"
---
# <a name="fatal-error-c1083"></a>错误 C1083

> 无法打开*filetype*文件: '*文件*:*消息*

找不到它需要的文件时，编译器将生成 C1083 错误。 有许多原因导致此错误。 不正确的包含搜索路径或文件缺失或名不符实了标头文件是最常见的原因，但其他文件类型和问题也会导致 C1083。 以下是一些为什么编译器将生成此错误的常见原因。

## <a name="the-specified-file-name-is-wrong"></a>指定的文件名错误

文件名可能键入有误。 例如，应用于对象的

`#include <algorithm.h>`

可能找不到你想要的文件。 大多数C++标准库标头文件没有.h 文件扩展名。 \<算法 > 标头将找不到此`#include`指令。 若要解决此问题，请验证输入正确的文件名称，如本例所示：

`#include <algorithm>`

某些 C 运行库标头位于标准包含目录的子目录中。 例如，若要包含 sys/types.h，必须包括 sys 子目录名称中的`#include`指令：

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>包含搜索路径中不包括的文件

此编译器无法使用 `#include` 或 `#import` 指令指示的搜索规则找到该文件。 例如，标头文件名称用引号引起来

`#include "myincludefile.h"`

这将告知编译器查找的第一次，包含源文件的相同目录中的文件，然后查找在指定的生成环境的其他位置中。 如果引号包含绝对路径，则编译器仅在该位置查找文件。 如果引号包含相对路径，则编译器在相对于源目录的目录中查找文件。

如果名称括在尖括号内

`#include <stdio.h>`

编译器遵循生成环境中，定义的搜索路径 **/I**编译器选项 **/X**编译器选项与**INCLUDE**环境变量。 有关详细信息，包括有关用于查找的文件的搜索顺序的特定详细信息，请参阅[#include 指令 (C /C++)](../../preprocessor/hash-include-directive-c-cpp.md)并[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。

如果包含文件位于相对于源目录，另一个目录并使用中的相对路径在 include 指令，您必须使用双引号而不是尖括号。 例如，如果在标头文件 myheader.h 的名为标头将项目源子目录中，然后此示例中未能找到该文件并将导致 C1083:

`#include <headers\myheader.h>`

但是，此示例的工作原理：

`#include "headers\myheader.h"`

相对路径也可以用于包含搜索路径上的目录。 如果添加到目录**INCLUDE**环境变量或设置为你**包含目录**路径在 Visual Studio 中，不要还向 include 指令添加路径的一部分。 例如，如果在标头位于 \path\example\headers\myheader.h，并添加到 \path\example\headers\ 你**包含目录**Visual Studio 中的路径，但你`#include`指令引用作为文件

`#include <headers\myheader.h>`

然后找不到该文件。 使用正确的路径相对于包含搜索路径中指定的目录。 在此示例中，可以将包含搜索路径更改为 \path\example\,或删除 headers\ 路径段从`#include`指令。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 Vcpkg

如果尝试将第三方库配置为生成的一部分时看到此错误，请考虑使用[Vcpkg](../../vcpkg.md)，视觉对象C++包管理器中，若要安装并生成库。 Vcpkg 支持大量且持续增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)，并设置所有配置属性和依赖项所需的成功生成项目的一部分。 有关详细信息，请参阅相关[可视化C++博客](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>该文件位于你的项目，但不是包含搜索路径

甚至当标头文件中列出**解决方案资源管理器**作为项目的一部分，会找到这些文件仅由编译器时它们由称为`#include`或`#import`指令源中的数据文件，并位于包含搜索路径。 不同种类的生成可能会使用不同搜索路径。 **/X**编译器选项可用于从包含搜索路径中排除目录。 这样不同的生成就可以使用具有相同名称、但保存在不同目录中的不同包含文件。 这是使用预处理器命令进行的条件编译的替代方法。 有关详细信息 **/X**编译器选项，请参阅[/X （忽略标准包含路径）](../../build/reference/x-ignore-standard-include-paths.md)。

若要修复此问题，请更改编译器用于搜索包含或导入的文件的路径。 新的项目使用默认值包括搜索路径。 您可能需要修改包含搜索路径添加为你的项目目录。 如果在命令行上编译，将添加到路径**INCLUDE**环境变量或 **/I**编译器选项来指定文件的路径。

若要在 Visual Studio 中设置包含目录路径，请打开项目的**属性页**对话框。 选择**VC + + 目录**下**配置属性**中的左窗格中，然后编辑**包含目录**属性。 有关通过 Visual Studio 中的编译器搜索的每个用户和每个项目目录的详细信息，请参阅[VC + + Directories Property Page](../../build/reference/vcpp-directories-property-page.md)。 有关详细信息 **/I**编译器选项，请参阅[/I （附加包含目录）](../../build/reference/i-additional-include-directories.md)。

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>未设置命令行包含或 LIB 环境

在命令行中调用编译器时，通常会使用环境变量来指定搜索路径。 如果所描述的搜索路径**INCLUDE**或**LIB**未正确设置环境变量，可以生成 C1083 错误。 我们强烈建议使用开发人员命令提示符快捷方式的基本命令行环境设置生成。 有关详细信息，请参阅[生成 C /C++命令行上](../../build/building-on-the-command-line.md)。 有关如何使用环境变量的详细信息，请参阅[如何：在生成中使用环境变量](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)。

## <a name="the-file-may-be-locked-or-in-use"></a>文件可能被锁定或正在使用

如果使用另一个程序来编辑或访问文件，它可能已锁定该文件。 请尝试关闭其他程序中的文件。 有时其他程序可以是 Visual Studio 本身，如果您正在使用并行编译选项。 如果关闭并行生成选项是错误消失，则出现此问题。 其他并行生成系统也可以具有此问题。 请注意设置文件和项目的依赖关系，以便生成顺序正确。 在某些情况下，请考虑创建一个中间项目强制为通用的文件，可能会生成多个项目的生成依赖项顺序。 有时防病毒程序暂时锁定最近更改的文件进行扫描。 如果可能，请考虑从防病毒扫描程序排除项目生成目录。

## <a name="the-wrong-version-of-a-file-name-is-included"></a>包含了错误版本的文件名

C1083 错误还可能指示包含了错误版本的文件。 例如，某个生成可能包含错误版本的文件，该文件的 `#include` 指令针对不是用于该生成的头文件。 例如，某些文件可能仅适用于 x86 版本，或调试版本。 当找不到头文件时，编译器会生成 C1083 错误。 此问题的解决方法是使用正确的文件，而不是向生成添加头文件或目录。

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>预编译头尚未预编译

当项目配置为使用预编译头时，必须创建相关 .pch 文件，以便可以编译使用头内容的文件。 例如，新项目在项目目录中自动创建 stdafx.cpp 文件。 先编译该文件以创建预编译的头文件。 在典型生成过程设计中，这是自动完成。 有关详细信息，请参阅[创建预编译标头文件](../../build/creating-precompiled-header-files.md)。

## <a name="additional-causes"></a>其他原因

- 已安装的 SDK 或第三方库，但 SDK 后未打开新的开发人员命令提示符窗口或安装库。 如果 SDK 或库将文件添加到**INCLUDE**路径，您可能需要打开新的开发人员命令提示符窗口，以拾取这些环境变量更改。

- 该文件使用托管的代码中，但编译器选项 **/clr**未指定。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

- 对文件进行编译使用不同**分析 /** 编译器选项设置不是使用预编译标头。 当一个项目的标头都要预编译时，应使用相同**分析 /** 设置。 有关详细信息，请参阅 [/analyze（代码分析）](../../build/reference/analyze-code-analysis.md)。

- 文件或目录创建的 Windows 子系统适用于 Linux、 启用每个目录的区分大小写，，指定的路径或文件的用例与路径或磁盘上的文件的大小写不匹配。

- 文件、目录或磁盘为只读。

- Visual Studio 或命令行工具没有足够权限来读取的文件或目录。 例如，这可能发生时的项目文件具有不同所有权比运行 Visual Studio 或命令行工具的过程。 有时可以修复此问题，以管理员身份运行 Visual Studio 或开发人员命令提示。

- 文件句柄不足。 关闭一些应用程序，然后重新编译。 这种情况一般不常见。 但是，在物理内存有限的计算机上生成大型项目时，可能会发生这种情况。

## <a name="example"></a>示例

下面的示例生成 C1083 错误时的标头文件`"test.h"`源目录中或包含搜索路径上不存在。

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

有关如何生成 C /C++项目在 IDE 或命令行和设置环境变量的信息请参阅[项目和生成系统](../../build/projects-and-build-systems-cpp.md)。

## <a name="see-also"></a>请参阅

- [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)

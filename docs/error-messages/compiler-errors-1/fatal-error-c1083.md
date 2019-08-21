---
title: 错误 C1083
ms.date: 09/01/2017
f1_keywords:
- C1083
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
ms.openlocfilehash: b982c3adf59789f6c48e7e0f54ed4e71539692ad
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630776"
---
# <a name="fatal-error-c1083"></a>错误 C1083

> 无法打开文件*类型*文件: "*file*": *message*

如果编译器找不到它所需的文件, 则会生成一个 C1083 错误。 导致此错误的可能原因有很多。 错误的包含搜索路径或缺少或 misnamed 头文件是最常见的原因, 但其他文件类型和问题也可能导致 C1083。 下面是编译器生成此错误的一些常见原因。

## <a name="the-specified-file-name-is-wrong"></a>指定的文件名错误

文件名可能键入有误。 例如，应用于对象的

`#include <algorithm.h>`

可能找不到你想要的文件。 大多数C++标准库头文件没有 .h 文件扩展名。 \<此`#include`指令找不到该算法 > 的标头。 若要解决此问题, 请验证是否输入了正确的文件名, 如以下示例中所示:

`#include <algorithm>`

某些 C 运行库标头位于标准包含目录的子目录中。 例如, 若要包含 sys/types .h, 则必须在`#include`指令中包含 sys 子目录名称:

`#include <sys/types.h>`

## <a name="the-file-is-not-included-in-the-include-search-path"></a>文件未包含在包括搜索路径中

此编译器无法使用 `#include` 或 `#import` 指令指示的搜索规则找到该文件。 例如, 当标头文件名用引号引起来时,

`#include "myincludefile.h"`

这会告知编译器首先在包含源文件的同一目录中查找文件, 然后在生成环境指定的其他位置查找文件。 如果引号包含绝对路径，则编译器仅在该位置查找文件。 如果引号包含相对路径，则编译器在相对于源目录的目录中查找文件。

如果名称由尖括号括起来,

`#include <stdio.h>`

编译器遵循由生成环境、 **/i**编译器选项、 **/x**编译器选项和**INCLUDE**环境变量定义的搜索路径。 有关详细信息, 包括有关用于查找文件的搜索顺序的特定详细信息, 请参阅[#include 指令 (CC++/)](../../preprocessor/hash-include-directive-c-cpp.md)和[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。

如果包含文件与源目录相对应的另一个目录, 并且在 include 指令中使用相对路径, 则必须使用双引号而非尖括号。 例如, 如果标头文件 myheader 位于名为 header 的项目源的子目录中, 则此示例将无法找到该文件并导致 C1083:

`#include <headers\myheader.h>`

但此示例起作用:

`#include "headers\myheader.h"`

相对路径也可用于包含搜索路径中的目录。 如果将目录添加到**include**环境变量或 Visual Studio 中的**包含目录**路径, 请不要将部分路径添加到 include 指令中。 例如, 如果标头位于 \path\example\headers\myheader.h, 则在 Visual Studio 中将 \path\example\headers\ 添加到 "**包含目录**" 路径, 但`#include`指令将该文件称为

`#include <headers\myheader.h>`

否则, 找不到该文件。 使用相对于在包括搜索路径中指定的目录的正确路径。 在此示例中, 可以将包含搜索路径更改为 \path\example\, , 或者`#include`从指令中删除标头 \ 路径段。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 Vcpkg

如果尝试在生成过程中配置第三方库时看到此错误, 请考虑使用[Vcpkg](../../vcpkg.md)(Visual C++ Package Manager) 来安装和生成库。 Vcpkg 支持较大和不断增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports), 并将成功生成所需的所有配置属性和依赖项设置为项目的一部分。 有关详细信息, 请参阅相关[的C++视觉对象博客](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="the-file-is-in-your-project-but-not-the-include-search-path"></a>文件在你的项目中, 但不包含搜索路径

即使头文件作为项目的一部分列在**解决方案资源管理器**中, 这些文件仅在源文件中由`#include`或`#import`指令引用时才由编译器找到, 并且位于包含搜索路径中。 不同种类的生成可能会使用不同搜索路径。 **/X**编译器选项可用于排除包含搜索路径中的目录。 这样不同的生成就可以使用具有相同名称、但保存在不同目录中的不同包含文件。 这是使用预处理器命令进行的条件编译的替代方法。 有关 **/x**编译器选项的详细信息, 请参阅[/X (忽略标准包含路径)](../../build/reference/x-ignore-standard-include-paths.md)。

若要修复此问题，请更改编译器用于搜索包含或导入的文件的路径。 新项目使用默认的包含搜索路径。 可能需要修改包含搜索路径才能为项目添加目录。 如果要在命令行上进行编译, 请将路径添加到**INCLUDE**环境变量或 **/i**编译器选项, 以指定文件的路径。

若要在 Visual Studio 中设置包含目录路径, 请打开项目的 "**属性页**" 对话框。 选择左窗格中 "**配置属性**" 下的 " **VC + + 目录**", 然后编辑 "**包含目录**" 属性。 若要详细了解由编译器在 Visual Studio 中搜索的每个用户和每个项目的目录, 请参阅 " [VC + + 目录" 属性页](../../build/reference/vcpp-directories-property-page.md)。 有关 **/i**编译器选项的详细信息, 请参阅[/I (附加包含目录)](../../build/reference/i-additional-include-directories.md)。

## <a name="the-command-line-include-or-lib-environment-is-not-set"></a>未设置命令行包含或 LIB 环境

在命令行中调用编译器时，通常会使用环境变量来指定搜索路径。 如果未正确设置**INCLUDE**或**LIB**环境变量描述的搜索路径, 则可能会生成 C1083 错误。 强烈建议使用开发人员命令提示符快捷方式为命令行生成设置基本环境。 有关详细信息, 请参阅[在命令C++行上生成 C/](../../build/building-on-the-command-line.md)。 有关如何使用环境变量的详细信息, 请参阅[如何:在生成](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)中使用环境变量。

## <a name="the-file-may-be-locked-or-in-use"></a>此文件可能已被锁定或正在使用中

如果正在使用其他程序编辑或访问该文件, 则该文件可能已锁定。 尝试关闭其他程序中的文件。 如果你使用的是并行编译选项, 有时其他程序可以是 Visual Studio 本身。 如果关闭 "并行生成" 选项会导致错误消失, 则这就是问题所在。 其他并行生成系统也可能出现此问题。 请小心设置文件和项目依赖项, 以便生成顺序正确。 在某些情况下, 请考虑创建一个中间项目, 为可能由多个项目生成的通用文件强制构建依赖项顺序。 有时, 防病毒程序暂时锁定最近更改过的文件以进行扫描。 如果可能, 请考虑从防病毒扫描程序中排除你的项目生成目录。

## <a name="the-wrong-version-of-a-file-name-is-included"></a>包含了错误版本的文件名

C1083 错误还可能指示包含了错误版本的文件。 例如，某个生成可能包含错误版本的文件，该文件的 `#include` 指令针对不是用于该生成的头文件。 例如, 某些文件可能仅适用于 x86 生成或用于调试生成。 当找不到头文件时，编译器会生成 C1083 错误。 此问题的解决方法是使用正确的文件，而不是向生成添加头文件或目录。

## <a name="the-precompiled-headers-are-not-yet-precompiled"></a>预编译头尚未预编译

当项目配置为使用预编译头时，必须创建相关 .pch 文件，以便可以编译使用头内容的文件。 例如, 在新项目的项目目录中自动创建*pch*文件 (Visual Studio 2017 及更早版本中的*stdafx.h* )。 先编译该文件以创建预编译的头文件。 在典型的生成过程设计中, 这是自动完成的。 有关详细信息, 请参阅[创建预编译头文件](../../build/creating-precompiled-header-files.md)。

## <a name="additional-causes"></a>其他原因

- 你已安装 SDK 或第三方库, 但你在安装 SDK 或库之后未打开新的开发人员命令提示符窗口。 如果 SDK 或库向**包含**路径添加文件, 则可能需要打开新的 "开发人员命令提示" 窗口来选取这些环境变量更改。

- 该文件使用托管代码, 但未指定编译器选项 **/clr** 。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。

- 使用不同于用于预编译标头的 **/analyze**编译器选项设置来编译文件。 预编译项目的标头时, 所有这些标头都应使用相同的 **/analyze**设置。 有关详细信息，请参阅 [/analyze（代码分析）](../../build/reference/analyze-code-analysis.md)。

- 文件或目录是由适用于 Linux 的 Windows 子系统创建的, 启用了每个目录的区分大小写, 而路径或文件的指定大小写与磁盘上的路径或文件的大小写不匹配。

- 文件、目录或磁盘为只读。

- Visual Studio 或命令行工具没有足够的权限读取文件或目录。 例如, 当项目文件的所有权不同于运行 Visual Studio 或命令行工具的进程时, 可能会发生这种情况。 有时, 可以通过以管理员身份运行 Visual Studio 或开发人员命令提示来解决此问题。

- 文件句柄不足。 关闭一些应用程序，然后重新编译。 这种情况一般不常见。 但是，在物理内存有限的计算机上生成大型项目时，可能会发生这种情况。

## <a name="example"></a>示例

下面的示例在源目录或包含搜索路径中`"test.h"`不存在标头文件时, 生成 C1083 错误。

```cpp
// C1083.cpp
// compile with: /c
#include "test.h"   // C1083 test.h does not exist
#include "stdio.h"  // OK
```

有关如何在 IDE 或命令行上C++生成 C/项目的信息, 以及有关设置环境变量的信息, 请参阅[项目和生成系统](../../build/projects-and-build-systems-cpp.md)。

## <a name="see-also"></a>请参阅

- [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)

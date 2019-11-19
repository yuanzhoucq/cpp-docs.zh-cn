---
title: 用于升级C++代码的 VISUAL Studio IDE 工具
description: Visual C++ Studio 中的代码编辑器和代码分析工具可帮助你实现基本C++代码的现代化。
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: 3f85b955b688489bfc04c4bfc0605201e883e3d4
ms.sourcegitcommit: 4dde7914608508e47c21cae03ac58fe953a0c29b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119632"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>用于升级C++代码的 VISUAL Studio IDE 工具

Visual Studio 可帮助你通过C++编译器选项、代码分析警告和编辑器功能（如快速修补程序、快速信息和增强的滚动条）升级旧版代码。 术语 "旧代码" 指以下任意类别：

- Microsoft C++编译器（MSVC）以前允许但不符合C++标准的代码。

   若要升级旧的不符合 MSVC 的代码，请打开[/permissive-](../build/reference/permissive-standards-conformance.md)编译器选项。 在代码编辑器中，不符合的用法的所有实例都带有红色波形曲线的下划线。 **错误列表**窗口中的错误消息包括如何修复错误的建议。 单击错误代码，以在文档中切换到其帮助页。 如果一次修复所有错误都不切实际，则可以通过打开 "**预许可**" 选项、修复一些错误，然后再次关闭该选项，来升级不符合的代码。 此代码将使用新的改进进行编译，你可以稍后返回并修复剩余问题。 请参阅[/permissive-](../build/reference/permissive-standards-conformance.md)页面，了解不相容 MSVC 代码的示例。

- 较早版本的C++标准中所允许的代码，但在更高版本中已弃用或删除。

   若要升级到较新的语言标准，请将[ C++语言标准](../build/reference/std-specify-language-standard-version.md)选项设置为所需的标准，并修复引发的任何编译错误。 通常，我们建议将 language standard 设置为[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)。 升级到较新的标准版本时引发的错误与使用 "**许可-** " 选项时引发的错误无关。

- 符合标准的所有版本的代码，但在现代C++上不再被视为最佳做法。

   若要确定建议更改的代码，请运行[代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="open-and-convert-a-legacy-project"></a>打开和转换旧项目

如果你的旧项目基于 Visual Studio 的较旧版本，你可以在 Visual Studio 2017 或 Visual Studio 2019 中打开它。 Visual Studio 会自动将其转换为当前项目架构，并支持所有最新的编译器和 IDE 功能。

![升级项目](media/upgrade-dialog-v142.png "升级项目")

有关详细信息，请[参阅C++从早期版本的 Visual Studio 升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)。

## <a name="search-the-code-base"></a>搜索基本代码

升级基本代码通常涉及搜索多个文件。 若要在基本代码中搜索任何内容，请按**Ctrl + T**打开 "**转到所有**搜索" 框。

![全部中转](media/go-to-all.png "全部中转")

若要缩小搜索范围，请键入一个1字母筛选器，后跟一个空格，然后是你要查找的内容。

## <a name="error-list"></a>错误列表

C++设置所需的语言标准和任何其他编译器选项（**Project** > **属性** > **常规**）后，按**Ctrl + Shift + B**来编译项目。 您可以在代码中的不同位置以红色波形曲线的形式查看一些错误和警告。 错误还会出现在**错误列表**中。 有关特定错误的详细信息，请单击错误代码以切换到文档中的帮助页。 以 "C" 开头的错误代码是编译器错误。 以 "MSB" 开头的代码是 MSBuild 错误，用于指示项目配置的问题。

![错误列表中的编译器和 MSBuild 错误](media/compiler-error-list.png "错误列表中的编译器和 MSBuild 错误")

## <a name="document-health-indicator"></a>文档运行状况指示器

编辑器底部的文档运行状况指示器显示了当前文档中的错误和警告数，并使你能够直接从一个警告/错误导航到下一个警告/错误。

![文档运行状况指示器](media/document-health-indicator.png "文档运行状况指示器")

在许多情况下，你可以在 Visual Studio 的 "更改历史记录" 和 "一致性改进" 文档中找到有关特定错误的详细信息。

- [C++一致性改进](../overview/cpp-conformance-improvements.md)
- [视觉C++更改历史记录 2003-2015](visual-cpp-change-history-2003-2015.md)
- [潜在的升级问题概述](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>使用代码分析实现代码的现代化

升级时，建议你在项目上运行代码分析，使代码至少符合 Microsoft 本机建议规则。 这些规则结合了 Microsoft 定义的规则和[ C++核心准则](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)的子集。 与此一致，你将大大减少或消除 bug 的常见来源，同时使你的代码更易于阅读，并使其更易于维护。 默认情况下，将启用使用 Microsoft 本机建议规则的代码分析。 您可以在 "**项目** > **属性**" 下启用其他规则 > **代码分析**"。 违反其中一个规则的代码会被标记为警告，并在代码编辑器中以绿色波浪线为下划线。 将鼠标悬停在波形曲线上，可查看描述该问题的**QuickInfo**工具提示。

![代码分析工具提示](media/code-analysis-tooltip.png "代码分析警告")

单击 "**代码**" 列中的筛选器图标，选择要显示的警告。

![错误列表中的代码分析筛选器](media/code-analysis-filter.png "错误列表中的代码分析筛选器")

类似于编译器错误，代码分析错误和警告也出现在**错误列表**中。

![错误列表中的代码分析警告](media/code-analysis-error-list.png "错误列表中的代码分析警告")

可以更改处于活动状态的规则，并创建自定义规则集。 有关使用代码分析的详细信息，请参阅[C/C++概述的代码分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

## <a name="use-quick-actions-to-modernize-code"></a>使用快速操作使代码实现现代化

代码编辑器为一些常见建议提供快速操作。 显示灯泡图标时，可以单击该图标以查看可用的快速操作。

### <a name="convert-macros-to-constexpr-functions"></a>将宏转换为 constexpr 函数

下图显示了如何使用称为 `AVERAGE`的宏，该宏具有默认语义着色。 图像还显示当鼠标光标悬停在其上方时显示的 QuickInfo 工具提示：

![QuickInfo 宏展开](media/macro-expansion-quick-info.png "QuickInfo 工具提示宏展开")

由于不鼓励使用宏C++，因此 Visual Studio 可以轻松地将宏转换为**constexpr**函数：

1. 右键单击 `AVERAGE`，然后选择 "**切换到定义**"。
2. 单击螺丝刀图标，然后选择 "**将宏转换为 constexpr** "

   ![用于 constexpr 的快速操作宏](media/quick-action-macro-to-constexpr.png "用于 constexpr 的快速操作宏")

此宏将被转换为，如下所示：

![constexpr 函数](media/constexpr-function.png "constexpr 函数")

和对 `AVERAGE` 的调用现在作为函数调用着色，快速信息工具提示显示函数的推导类型：

![constexpr 函数调用](media/constexpr-function-call.png "constexpr 函数调用")

### <a name="initialize-variables"></a>初始化变量

未初始化的变量可以保存导致严重错误的随机值。 代码分析对这些实例进行标记，编辑器提供了一个快速操作：

![初始化变量](media/init-variable.png "初始化变量快速操作")

### <a name="convert-to-raw-string-literal"></a>转换为原始字符串文本

与带有嵌入转义符的字符串相比，原始字符串文本比较容易出错且更方便类型。 右键单击字符串，然后选择 "**快速操作**"，将其转换为原始字符串文本。

![原始字符串文本](media/raw-string-literal.png "原始字符串文本")

字符串转换为： `R"(C:\Users\bjarnes\demo\output.txt)"`。

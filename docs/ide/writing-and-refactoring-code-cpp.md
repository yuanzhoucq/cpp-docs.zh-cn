---
title: 在 Visual Studio 中编辑和重构 C++ 代码
description: 使用 Visual Studio 中的 C++ 代码编辑器来设置代码格式以及导航、理解和重构代码。
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.topic: overview
ms.openlocfilehash: da3f4e7d783561dba8250652a0715e51e71cc387
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438161"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>在 Visual Studio 中编辑和重构 C++ 代码

Visual Studio 提供了多种用于帮助编写、编辑和重构代码的工具。

##  <a name="intellisense"></a>IntelliSense

IntelliSense 是一款功能强大的代码完成工具，可在键入时建议符号和代码片段。 Visual Studio 中的 C++ IntelliSense 实时运行，并且会在更新代码库时对其进行分析并提供建议。 在键入更多字符时，推荐结果列表会缩小。

![C&#43;&#43; 成员下拉列表](../ide/media/cpp-statement-completion.png)

一些符号会自动省略，帮助减少结果。 例如，从类外部访问类对象的成员时，将无法查看默认或受保护的成员（如果不在子类的上下文中）。 可使用底部的按钮调整筛选。

从下拉列表中选择符号后，可以使用**Tab 键**、 **Enter**键或其他提交字符之一（默认为： `{ } [ ] ( ) . , : ; + - * / % & | ^ ! = ? @ # \`）自动完成。 要在此列表中添加或删除字符，请在“快速启动”（Ctrl + Q）中搜索“IntelliSense”，然后选择“文本编辑器”>“C/C++”>“高级”选项。 “成员列表提交字符”选项允许使用所需更改自定义列表。

“成员列表筛选模式”选项控制显示的 IntelliSense 自动完成建议的类型。 默认情况下，它设置为“模糊”。 在模糊搜索中，如果你有名为 MyAwesomeClass 的符号，则可以键入“MAC”并在自动完成建议中查找该类。 模糊算法设置了符号要显示在列表中所必须满足的最小阈值。 智能筛选显示包含与键入的内容匹配的 substring 的所有符号。 前缀筛选搜索以键入的内容开头的字符串。

有关 C++ IntelliSense 的详细信息，请参阅 [Visual C++ IntelliSense](/visualstudio/ide/visual-cpp-intellisense) 和[配置用于 IntelliSense 的 C++ 项目](/visualstudio/ide/visual-cpp-intellisense-configuration)。

## <a name="intellicode"></a>IntelliCode

IntelliCode 是 AI 辅助的 IntelliSense。 它将最有可能的候选项置于完成列表的顶部。 IntelliCode 建议基于 GitHub 上的数千个开放源代码项目，其中每个项目都有 100 多个星级。 在与代码的上下文相结合时，将定制完成列表以推荐常见做法。

在编写 C++ 时，IntelliCode 可在使用 C++ 标准库等热门库时提供协助。 代码的上下文用于首先提供最有用的建议。 在以下示例中，`size` 成员函数通常与 `sort` 函数一起使用，因此它显示在结果列表的顶部。

![C&#43; &#43; IntelliCode](../ide/media/intellicode-cpp.png "C++IntelliCode")

::: moniker range="vs-2019"

在 Visual Studio 2019 中，IntelliCode 可用作 C++ 桌面开发工作负载中的可选组件。 要确保 IntelliCode 对 C++ 可用，请转到“工具” **“选项”** “IntelliCode” > “常规”并将“C++ 基础模型”设置为“启用” >  > 。

::: moniker-end

::: moniker range="vs-2017"

在 Visual Studio 2017 中，IntelliCode 可用作 Visual Studio Marketplace 中的扩展。

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>预测 IntelliSense（试验性）

“预测 IntelliSense”是一项试验性功能，它使用上下文感知来限制 IntelliSense 下拉列表中显示的结果数。 该算法会应用类型匹配，以便仅显示与预期类型匹配的结果。 在最简单的情况下，如果键入 `int x =` 并调用 IntelliSense 下拉列表，则只会看到整数或返回整数的函数。 默认情况下，此功能处于关闭状态，因为它仍处于开发阶段。 它最适合用于全局符号；尚不支持成员函数。 可以通过在“快速启动”中键入“预测”或转到“工具” **“选项”** ”文本编辑器” **”C/C++”** “试验性” > “启用预测 IntelliSense”来将其打开 >  >  >  > 。

若要覆盖**预测 IntelliSense**并显示较长的列表，请按**Ctrl + J**。如果**预测 IntelliSense**为 on，则调用**Ctrl + J**将删除预测筛选器。 再次按 Ctrl + J 会从相关成员列表结果中删除辅助功能筛选器。 IntelliSense 下拉列表下的 "（[+]）" 按钮执行与**Ctrl + J**相同的操作。将鼠标悬停在按钮上，以查看有关正在显示的内容的工具提示信息。

![C&#43; &#43;预测 IntelliSense](../ide/media/predictive-intellisense-cpp.png "预测 IntelliSense")

上面的屏幕截图显示了下拉列表下的几个按钮。 它们为不同类型的结果启用了 IntelliSense 筛选器：

- 变量和常量
- 函数
- 类型
- 宏
- 枚举
- 命名空间

仅当某一按钮与当前 IntelliSense 会话相关时，才会显示该按钮。 通常不会同时看到所有按钮。

## <a name="template-intellisense"></a>模板 IntelliSense

当脱字号位于模板定义中时，系统会显示“模板栏”，让你能够为 IntelliSense 提供示例模板参数。 

![C&#43; &#43;模板 IntelliSense 显示现有的实例化](../ide/media/template-intellisense-cpp-1.png "模板 IntelliSense 显示现有的实例化")

单击 " **\<t >** " 图标以展开/折叠**模板栏**。 单击铅笔图标或双击“模板栏”，打开“编辑”窗口。 

![C&#43; &#43;模板 IntelliSense](../ide/media/template-intellisense-cpp-3.png "模板 IntelliSense")

在窗口中进行的编辑将直接应用于源代码，以便可以实时查看效果。 

模板栏可以根据代码中的实例化自动填充候选项。 单击“添加所有现有实例化”，查看已用于在整个代码库中实例化模板的所有实际参数的列表。

![C&#43; &#43;模板 IntelliSense 结果列表](../ide/media/template-intellisense-cpp-2.png "模板 IntelliSense 结果列表")

编辑器底部的窗口显示了每个实例化的位置及其参数。

![C&#43; &#43;模板 IntelliSense 实例化映射](../ide/media/template-intellisense-cpp-4.png "模板 IntelliSense 实例化映射")

“模板栏”信息被视为特定于用户。 该信息存储在 .vs 文件夹中，并且不提交给源代码管理。

##  <a name="error-squiggles-and-quick-fixes"></a>错误波浪线和快速修复

如果编辑器检测到代码出现问题，它将在问题下方添加彩色波浪线。 红色波浪线表示无法编译的代码。 绿色波浪线表示仍可能很严重的其他类型的问题。 可以打开“错误列表”窗口，获取有关问题的详细信息。

对于某些类型的错误以及常见的编码模式，编辑器将以灯泡（在将鼠标悬停在波浪线上时出现）的形式提供“快速修复”。 单击向下箭头查看建议。 

以下示例中声明了 `vector` 但未找到定义，因此编辑器会包含必需的头文件：

![C&#43; &#43;快速修复](../ide/media/quick-fix-for-header-cpp.png "C++快速修复")

编辑器还提供了快速修复，以获得一些重构机会。 例如，如果在头文件中声明一个类，Visual Studio 将会在单独的 .cpp 文件中为其创建定义。 

![C&#43; &#43;快速修复](../ide/media/quick-fix.png "C++快速修复")

## <a name="change-tracking"></a>更改跟踪

每次对文件进行更改时，左侧都将出现一个黄色栏，表示所做的更改未保存。 保存文件时，该栏将变为绿色。 只要文档在编辑器中打开，就会保留绿色和黄色栏。 它们代表自上次打开文档以来所做的更改。

![C&#43; &#43;更改跟踪](../ide/media/change-tracking-cpp.png "更改跟踪")

## <a name="move-code"></a>移动代码

可以通过选中代码，按住 Alt 并按向上/向下箭头键来上下移动代码行。

##  <a name="insert-snippets"></a>插入代码片段

代码片段是一段预定义的源代码。 在单个点上或在选定文本上右键单击以插入代码片段或用代码片段环绕选定文本。 下图显示用 for 循环环绕选定语句的三个步骤。 最终图像中的黄色突出显示是使用 tab 键访问的可编辑字段。 有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。

![C&#43; &#43;插入代码片段&#45;下拉](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>添加类

在“项目”菜单或“解决方案资源管理器”的上下文菜单中添加新类：

![在 C 中添加新类&#43;&#43;](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

也可使用类向导来修改或检查现有类。

![C&#43;&#43; 类向导](../ide/media/vs2017-class-wizard.png)

有关详细信息，请参阅[用代码向导添加功能 (C++)](../ide/adding-functionality-with-code-wizards-cpp.md)。

##  <a name="refactoring"></a>重构

可在“快速操作”上下文菜单下，或者通过单击编辑器中的[灯泡](/visualstudio/ide/perform-quick-actions-with-light-bulbs)使用重构。  有的也可从“编辑”>“重构”菜单访问。  这些功能包括：

* [重命名](refactoring/rename.md)
* [提取函数](refactoring/extract-function.md)
* [实现纯虚方法](refactoring/implement-pure-virtuals.md)
* [创建声明/定义](refactoring/create-declaration-definition.md)
* [移动函数定义](refactoring/move-definition-location.md)
* [转换为原始字符串文本](refactoring/convert-to-raw-string-literal.md)
* [更改签名](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>使用 ClangFormat 和 EditorConfig 强制执行代码样式

Visual Studio 2017 及更高版本附带对 [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)（一种基于 Clang/LLVM 的常用 C++ 代码格式化实用工具）的内置支持。 在[快速启动](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box)中键入“ClangFormat”，将其设置为使用以下某种常用格式：

- LLVM
- Google
- Chromium
- Mozilla
- WebKit
- Visual Studio

还可以提供自己的 .clang 格式或 _clang 格式文件，以将自定义规则应用于同一级别或更低级别的所有代码文件。

这些文件可以通过源代码管理轻松共享，因此可以在整个开发团队中强制执行编码约定。

![C&#43; &#43; Clang 格式](../ide/media/clang-format-cpp.png "Clang 格式")

Visual Studio 2017 及更高版本还支持工作方式类似的 [EditorConfig](https://editorconfig.org/)。 但是，ClangFormat 的样式选项比 EditorConfig 要多，包括特定于 C++ 的规则。 使用 EditorConfig 创建 .editorconfig 文件，并将其置于代码库的不同文件夹中，以指定这些文件夹及其子文件夹的代码样式。 .editorconfig 文件会取代父文件夹中的任何其他 .editorconfig 文件，并覆盖通过“工具” **“选项”配置的任何格式设置** > 。 可以为制表符和空格、缩进大小等设置规则。 有关详细信息，请参阅[使用 EditorConfig 创建可移植的自定义编辑器设置](/visualstudio/ide/create-portable-custom-editor-options)。

## <a name="other-formatting-options"></a>其他格式设置选项

“快速启动”搜索框中提供了用于查找设置或工具的最快方式。 它位于主菜单上。 只需开始键入，自动完成列表即可筛选结果。

![Visual Studio 快速启动](../ide/media/vs2015_cpp_quick_launch.png "快速启动")

若要设置缩进、括号补全和着色等格式设置选项，请在“快速启动”窗口中键入“C++ 格式设置”。

![C++ 格式设置选项](media/cpp-formatting-options.png)

其他格式设置选项位于主菜单中的“编辑” **“高级”下** > 。

![C++ 高级编辑选项](media/edit-advanced-cpp.png)

启用和配置 C++ 特定编辑功能的选项位于“工具” **“选项”** “文本编辑器” > “C/C++”下 >  > 。 选择想要设置的选项之后，在焦点位于对话框上时按 F1 可获取更多帮助。 如需通用代码格式设置选项，请在“快速启动”中键入 `Editor C++`。

![Visual Studio Tools > 选项](../ide/media/tools-options.png "编辑器选项")

在[文本编辑器 C++ 实验](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental)对话框中可找到实验性功能，未来版本的 Visual Studio 中不一定包含这些功能。 在 Visual Studio 2017 及更高版本中，可在此对话框中启用“预测 IntelliSense”。

## <a name="see-also"></a>另请参阅

[阅读并理解 C++ 代码](read-and-understand-code-cpp.md)</br>
[在 Visual Studio 中导航 C++ 代码库](navigate-code-cpp.md)</br>
[使用适用于 C++ 的 Live Share 进行协作](live-share-cpp.md)

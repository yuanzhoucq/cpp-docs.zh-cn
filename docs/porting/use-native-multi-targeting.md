---
title: 使用 Visual Studio 中的本机多目标来生成旧项目
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: 14100a70fa3bb883d257017eaf9174c5340317b4
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404803"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>使用 Visual Studio 中的本机多目标来生成旧项目

通常，建议在安装最新版本的 Visual Studio 时更新项目。 更新项目和代码所要花费的成本通常会大过新 IDE、编译器、库和工具所带来的好处。 但是，我们知道你可能无法更新某些项目。 你可能会有与较旧库或平台相关的二进制文件，因为无法升级这些库或平台。 你的代码可能使用非标准的语言构造，如果移动到更新的编译器，构造会发生中断。 代码可能依赖于为特定 Visual C++ 版本编译的第三方库。 或者可能需要为某些组织生成库，而这些组织必须以某个 Visual C++ 的特定较旧版本为目标。

幸运的是，可以使用 Visual Studio 2017 和 Visual Studio 2015 生成面向较旧编译器工具集和库的项目。 不必升级 Visual Studio 2010、Visual Studio 2012、Visual Studio 2013 或 Visual Studio 2015 项目即可利用 IDE 中的新功能：

- 新的 C++ 重构功能和编辑器实验功能
- 新的诊断工具调试器窗口和错误列表窗口
- 改进的断点、异常窗口和新的 PerfTips
- 新的代码导航和搜索工具
- 新的 C++ 快速修复和 Productivity Power Tools 扩展。

还可以面向 Visual Studio 2008 项目，但不能一成不变地使用这些项目。 有关详细信息，请参阅**Visual Studio 2008 说明**部分。

最新版本的 Visual Studio 支持项目的本机多目标和往返。 本机多目标是一种功能，即最新的 IDE 使用 Visual Studio 旧版本安装的工具集进行生成。 往返是一种功能，即最新的 IDE 可加载由 IDE 旧版本创建的项目，而无需对项目进行任何更改。 如果并行安装最新版本和现有版本的 Visual Studio，则可以配合使用新版本的 IDE 与现有版本的编译器和工具，来生成项目。 团队的其他成员可以继续在旧版本的 Visual Studio 中使用项目。

使用较旧的工具集时，可以利用许多最新的 IDE 功能，但不能利用 C++ 编译器、库和生成工具中的最新改进。 例如，将无法使用新的语言一致性改进、新调试和代码分析功能，或实现更快的最新工具集生成吞吐量。 也有一些 IDE 功能与旧的工具集不兼容。 例如，内存探查器中可能缺少类型信息，并且重构操作**转换为原始字符串文本**会生成在使用 Visual Studio 2012 或更低版本的工具集时不进行编译的 C + 11 兼容代码。

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>如何使用 Visual Studio 中的本机多目标

并行安装 Visual Studio 和较旧版本后，在 Visual Studio 的新版本中打开现有项目。 加载项目时，Visual Studio 会询问是否要对其进行升级以使用最新的 C++ 编译器和库。 由于希望项目保留旧版编译器和库，因此选择“取消”**** 按钮。

Visual Studio 会持续提示升级项目。 为避免在每次加载项目时看到升级对话框，可在项目中或在项目导入的 .props 或 .targets 文件中定义以下属性：

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

如果想升级项目，必须删除此属性。

如果选择不升级，Visual Studio 不会对解决方案或项目文件进行更改。 生成项目时，生成的二进制文件与使用旧版本的 Visual Studio 生成的二进制文件完全兼容。 这是因为 Visual Studio 使用的 C++ 编译器和链接的库与旧版 IDE 所随附的相同。 这也是为什么如果选择“取消”****，升级对话框会警告保留安装较旧的 Visual Studio 版本。

## <a name="instructions-for-visual-studio-2008"></a>有关 Visual Studio 2008 的说明

Visual Studio 2008 具有其自己的用于 c + + 的专用生成系统（称为**VCBuild**）。 从 Visual Studio 2010 开始，Visual Studio C++ 项目改为使用 **MSBuild**。 这意味着，无论是永久性升级还是多目标升级，都必须执行更新步骤，以在最新版本的 Visual Studio 中生成 Visual Studio 2008 项目。 更新的项目仍然会生成与使用 Visual Studio 2008 IDE 创建的二进制文件完全兼容的二进制文件。

首先，除了当前版本的 Visual Studio 之外，还必须将 Visual Studio 2010 安装在安装 Visual Studio 2008 的计算机上。 只有 Visual Studio 2010 安装目标 Visual Studio 2008 项目所需的**MSBuild**脚本。

接下来，必须将 Visual Studio 2008 解决方案和项目更新到当前版本的 Visual Studio。 建议在升级之前创建项目和解决方案文件的备份。 若要开始升级过程，请在当前版本的 Visual Studio 中打开解决方案。 获取升级提示时，请查看显示的信息，然后选择“确定”**** 以开始升级。 如果解决方案中有多个项目，则必须更新，向导使用现有 .vcproj 文件并行创建新的 .vcxproj 项目文件。 只要你也有原始 .sln 文件的副本，升级对你现有的 Visual Studio 2008 项目就没有其他影响。

> [!NOTE]
> 以下步骤仅适用于多目标方案。 如果要将项目永久升级到更高版本的工具集，则下一步是保存项目，在 Visual Studio 2019 中打开它，并解决出现的生成问题。

升级完成后，如果日志报告中有关于任何项目的错误或警告，请仔细查看。 从**VCBuild**到**MSBuild**的转换可能会导致问题。 请确保已了解并执行报告中列出的所有操作项。 有关在将**VCBuild**转换为**MSBuild**时可能出现的升级日志报表和问题的详细信息，请参阅此[c + + 本机多目标](https://devblogs.microsoft.com/cppblog/c-native-multi-targeting/)博客文章。

项目升级完成且已更正日志文件中的所有问题后，解决方案才真正面向最新的工具集。 最后一步是更改解决方案中每个项目的属性以使用 Visual Studio 2008 工具集。 在当前版本的 Visual Studio 中加载解决方案后，针对解决方案中每个项目，打开项目的“属性页”**** 对话框：右键单击“解决方案资源管理器”**** 中的项目，然后选择“属性”****。 在“属性页”**** 对话框中，将“配置”**** 下拉值更改为“所有配置”****。 在“配置属性”**** 下，选择“常规”****，然后将“平台工具集”**** 更改为 **Visual Studio 2008 (v90)**。

进行此更改后，在当前版本的 Visual Studio 中构建解决方案时，使用 Visual Studio 2008 编译器和库生成项目二进制文件。

## <a name="install-an-older-visual-studio-toolset"></a>安装较旧版本的 Visual Studio 工具集

可能会有无法或不打算升级的旧版 Visual Studio C++ 项目，但没有与项目匹配的平台工具集版本。 在这种情况下，为了获得工具集，可以安装所需版本的免费 Visual Studio 社区版或速成版。 从 Visual Studio 2008 开始，每个版本的 Visual Studio 都可以安装从当前 Visual Studio 面向该版本时所需的编译器、工具和库。 搜索 Microsoft 下载中心以查找和下载 Visual Studio 的特定版本。 请确保在安装过程中选择 C++ 安装选项。 安装完成后，运行该版本的 Visual Studio 以安装任何更新。 同时查找可能需要的任何 Windows 更新更改。 此更新检查过程可能需要重复多次以获取每个更新。

有关当前可用的下载，请参阅[下载较旧的 Visual Studio 软件](https://visualstudio.microsoft.com/vs/older-downloads/)。

安装这些产品后，“属性页”对话框中的“平台工具集”属性下拉列表自动更新为显示可用工具集********。 现在，可以使用最新版 Visual Studio 为这些较旧版本的工具集生成项目，而无需对这些旧版本进行转换或升级。

## <a name="see-also"></a>另请参阅

[从 Visual C++ 早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual Studio 中的 C++ 符合性改进](../overview/cpp-conformance-improvements.md)

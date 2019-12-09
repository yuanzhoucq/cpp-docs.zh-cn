---
title: 在 Visual Studio 中安装 C++ 支持
description: 安装 visual Studio for Visual Studio 支持C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: a20a2432cbf8c4dc5f211f6f483c0084888f1199
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857159"
---
# <a name="install-c-support-in-visual-studio"></a>在 Visual Studio 中安装 C++ 支持

如果尚未下载并安装 Visual Studio 和 Visual C++ tools，请参阅下面的入门指南。

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 安装

欢迎使用 Visual Studio 2019！ 在此版本中，可轻松选择并仅安装所需功能。 并且由于其最小占用减小，因此其安装速度快且对系统的影响极小。

> [!NOTE]
> 本主题适用于在 Windows 上安装 Visual Studio。 [Visual Studio Code](https://code.visualstudio.com/)是一种轻型的跨平台开发环境，在 Windows、Mac 和 Linux 系统上运行。 Microsoft [C/C++ for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)扩展支持 IntelliSense、调试、代码格式设置、自动完成。 Visual Studio for Mac 不支持 Microsoft C++，但支持 .net 语言和跨平台开发。 有关安装说明，请参阅[安装 Visual Studio for Mac](/visualstudio/mac/installation/)。

想要详细了解此版本的其他新增功能？ 请参阅 Visual Studio[发行说明](/visualstudio/releases/2019/release-notes/)。

准备安装？ 我们将逐步引导你完成安装。

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>第 1 步 - 确保计算机支持 Visual Studio

开始安装 Visual Studio 前：

1. 查看[系统要求](/visualstudio/releases/2019/system-requirements)。 这些要求有助于了解计算机是否支持 Visual Studio 2019。

1. 应用最新的 Windows 更新。 这些更新可确保计算机包含最新的安全更新程序和 Visual Studio 所需的系统组件。

1. 重新启动。 重新启动可确保挂起的任何安装或更新都不会影响 Visual Studio 安装。

1. 释放空间。 通过运行磁盘清理应用程序等方式，从 %SystemDrive% 删除不需要的文件和应用程序。

有关使用 Visual Studio 2019 并排运行 Visual Studio 先前版本的问题，请参阅 [Visual Studio 2019 平台目标和兼容性](/visualstudio/releases/2019/compatibility/)页面。

### <a name="step-2---download-visual-studio"></a>第 2 步 - 下载 Visual Studio

接下来，下载 Visual Studio 引导程序文件。 为此，请选择下面的按钮，选择所需的 Visual Studio 版本，选择“保存”，然后选择“打开文件夹”。

 > [!div class="button"]
 > [下载 Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>第 3 步 - `打开` Visual Studio 安装程序

运行引导程序文件以安装 Visual Studio 安装程序。 这个新的轻型安装程序包括安装和自定义 Visual Studio 所需的一切。

1. 在“下载”文件夹中，双击与下列文件之一匹配或类似的引导程序文件：

   * 对于 Visual Studio Community，请运行 **vs_community.exe**
   * 对于 Visual Studio Professional，请运行 **vs_professional.exe**
   * 对于 Visual Studio Enterprise，请运行 **vs_enterprise.exe**

   如果收到用户帐户控制通知，请选择“是”。

1. 我们会要求确认 Microsoft [许可条款](https://visualstudio.microsoft.com/license-terms/)和 Microsoft [隐私声明](https://privacy.microsoft.com/privacystatement)。 选择“继续”。

### <a name="step-4---choose-workloads"></a>第 4 步 - 选择工作负载

安装安装程序后，可以通过选择所需的*工作负荷*或功能集来使用它来自定义安装。 操作方法如下。

1. 在“安装 Visual Studio”屏幕中找到所需的工作负载。

   ![Visual Studio 2019：安装工作负荷](../get-started/media/vs-installer-workloads.png)

   对于核心C++支持，请选择 "桌面开发C++" 工作负载。 它附带默认核心编辑器，该编辑器针对超过 20 种语言提供基本代码编辑支持，能够打开和编辑任意文件夹中的代码（而无需使用项目），还提供集成的源代码管理。

   其他工作负荷支持其他类型C++的开发。 例如，选择 "通用 Windows 平台开发" 工作负荷，以创建使用 Microsoft Store 的 Windows 运行时的应用。 选择 "使用C++游戏开发" 创建使用 DirectX、Unreal 和 cocos2d 为后盾的游戏。 选择 "通过C++linux 开发" 来面向 linux 平台，包括 IoT 开发。

   "**安装详细信息**" 窗格列出了每个工作负荷安装的包含组件和可选组件。 您可以选择或取消选择此列表中的可选组件。 例如，若要使用 Visual Studio 2017 或2015编译器工具集来支持开发，请选择 MSVC v141 或 MSVC v140 可选组件。 可以添加对 MFC、实验性模块语言扩展、IncrediBuild 等的支持。

1. 选择所需的工作负荷和可选组件后，请选择 "**安装**"。

    接下来，会出现多个显示 Visual Studio 安装进度的状态屏幕。

> [!TIP]
> 在安装之后，可以随时安装最初未安装的工作负荷或组件。 如果已打开 Visual Studio，请转到“工具” > “获取工具和功能...”，这会打开 Visual Studio 安装程序。 或者，从“开始”菜单打开“Visual Studio 安装程序”。 在此处可以选择要安装的工作负载或组件。 然后，选择“修改”。

### <a name="step-5---choose-individual-components-optional"></a>第 5 步 - 选择各个组件（可选）

如果不想使用工作负载功能来自定义 Visual Studio 安装，或者要添加比工作负荷安装更多的组件，则可以通过从 "**单个组件**" 选项卡中安装或添加单个组件来实现此目的。选择所需内容，然后按照提示进行操作。

  ![Visual Studio 2019-安装单个组件](../get-started/media/vs-installer-individual-components.png "安装 Visual Studio 单个组件")

### <a name="step-6---install-language-packs-optional"></a>第 6 步 - 安装语言包（可选）

默认情况下，安装程序首次运行时会尝试匹配操作系统语言。 若要以所选语言安装 Visual Studio，请从 Visual Studio 安装程序中选择“语言包”选项卡，然后按照提示进行操作。

  ![Visual Studio 2019-安装语言包](../get-started/media/vs-installer-language-packs.png "安装 Visual Studio 语言包")

#### <a name="change-the-installer-language-from-the-command-line"></a>从命令行更改安装程序语言

更改默认语言的另一种方法是从命令行运行安装程序。 例如，可以通过运行以下命令来强制安装程序用英语运行：`vs_installer.exe --locale en-US`。 安装程序将在下一次运行时记住此设置。 安装程序支持以下语言标记：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

### <a name="step-7---change-the-installation-location-optional"></a>第 7 步 - 更改安装位置（可选）

可减少系统驱动器上 Visual Studio 的安装占用。 可以选择将下载缓存、共享组件、SDK 和工具移动到不同驱动器，并将 Visual Studio 安装在其运行速度最快的驱动器上。

  ![Visual Studio 2019-更改安装位置](../get-started/media/vs-installer-installation-locations.png "更改安装位置")

> [!IMPORTANT]
> 仅当首次安装 Visual Studio 时，才可选择其他驱动器。 如果已安装 Visual Studio 并要更改驱动器，则必须先将其卸载然后再重新安装。

### <a name="step-8---start-developing"></a>第 8 步 - 开始开发

1. 在 Visual Studio 安装完成后，选择“启动”按钮，开始使用 Visual Studio 进行开发。

1. 在“开始”窗口上，选择“创建新项目”。

1. 在搜索框中，输入要创建的应用类型，查看可用模板列表。 模板列表取决于在安装期间选择的工作负载。 若要查看其他模板，请选择其他工作负载。

   此外，还可使用“语言”下拉列表筛选搜索特定编程语言。 也可使用“平台”列表和“项目类型”列表进行筛选。

1. Visual Studio 会打开新的项目，然后便可开始编码！

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安装

在 Visual Studio 2017 中，可以轻松地选择并仅安装所需的功能。 并且由于其最小占用减小，因此其安装速度快且对系统的影响极小。

### <a name="prerequisites"></a>先决条件

- 宽带 Internet 连接。 Visual Studio 安装程序可以下载几千兆字节的数据。

- 运行 Microsoft Windows 7 或更高版本的计算机。 建议使用 Windows 10 以实现最佳开发体验。 安装 Visual Studio 前，请确保向系统应用最新更新。

- 足够的可用磁盘空间。 Visual Studio 至少需要 7 GB 磁盘空间，如果安装了很多常见选项，可能需要 50 GB 或更大的空间。 建议将其安装在 C: 驱动器上。

有关磁盘空间和操作系统要求的详细信息，请参阅 [Visual Studio 产品系列系统要求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安装程序会报告所选选项需要多少磁盘空间。

### <a name="download-and-install"></a>从

1. 下载最新的适用于 Windows 的 Visual Studio 2017 安装程序。

   > [!div class="nextstepaction"]
   > [安装 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 适用于个体开发者、课堂学习、学术研究和开放源代码开发。 对于其他用途，请安装 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 找到你下载的安装程序文件并运行。 它可能会在浏览器中显示，或者，可以在“下载”文件夹中找到它。 安装程序需要管理员权限才能运行。 可能会看到**用户帐户控制**对话框，要求授予安装程序对系统进行更改的权限; 请选择**是**。 如果遇到问题，请在文件资源管理器中找到下载的文件，右键单击 "安装程序" 图标，然后从上下文菜单中选择 "以**管理员身份运行**"。


   ![下载并安装 Visual Studio 安装程序](media/vscpp-concierge-run-installer.gif "下载并安装 Visual Studio 安装程序")

1. 安装程序提供工作负载列表，即一组用于特定开发领域的相关选项。 现在，对 C++ 的支持是可选工作负荷（默认情况下不会安装）的一部分。

   ![桌面开发与C++工作负荷](media/desktop-development-with-cpp.png "使用 C++ 的桌面开发")

   对于C++""，请选择 "带有**C++** 工作负荷的桌面开发"，然后选择 "**安装**"。

   ![安装具有C++工作负载的桌面开发](media/vscpp-concierge-choose-workload.gif "安装具有C++工作负载的桌面开发")

1. 安装完成后，选择 "**启动**" 按钮以启动 Visual Studio。

   首次运行 Visual Studio 时，系统会要求使用 Microsoft 帐户进行登录。 如果没有此类帐户，则可以免费创建一个。 还必须选择一个主题。 别担心，后期可以根据需要进行更改。

   第一次运行时，Visual Studio 可能需要几分钟才能使用。下面是快速延时的演示：

   ![Visual Studio 2017 登录](media/vscpp-quickstart-first-run.gif "Visual Studio 2017 登录")

   再次运行 Visual Studio 时，Visual Studio 的启动速度要快得多。

1. Visual Studio 打开时，检查标题栏中的标志图标是否突出显示：

   ![Visual Studio 2017 通知标志](media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知标志")

   如果突出显示，请选择它以打开 "**通知**" 窗口。 如果有任何适用于 Visual Studio 的更新，建议立即安装。 安装完成后，请重启 Visual Studio。

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安装

若要安装 Visual Studio 2015，请转到[下载较旧版本的 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 运行安装程序并选择“自定义安装”，然后选择 C++ 组件。 要向现有 Visual Studio 2015 安装添加 C++ 支持，请单击 Windows 开始按钮，然后键入**添加或删除程序**。 从结果列表中打开该程序，然后在已安装的程序列表中找到你的 Visual Studio 2015 安装。 双击它，然后选择**修改**并选择要安装的 Visual C++ 组件。

一般情况下，强烈建议使用 Visual Studio 2017，即使需要使用 Visual Studio 2015 编译器编译代码。 有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](../porting/use-native-multi-targeting.md)。

::: moniker-end

当 Visual Studio 正在运行时，您可以继续进行下一步。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [创建C++项目](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />

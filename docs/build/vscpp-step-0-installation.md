---
title: 在 Visual Studio 中安装 C++ 支持
description: 安装 Visual Studio 支持视觉对象C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58870775"
---
# <a name="install-c-support-in-visual-studio"></a>在 Visual Studio 中安装 C++ 支持

如果您还没有下载并安装 Visual Studio 和视觉对象C++工具还，此处的入门。

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 安装

欢迎使用 Visual Studio 2019 ！ 在此版本中，很容易选择并安装所需的功能。 并且由于其降低的最小内存需求量，安装速度快、 系统影响更小。

> [!NOTE]
> 本主题适用于 Windows 上的 Visual Studio 的安装。 [Visual Studio Code](https://code.visualstudio.com/)是一个轻型的跨平台开发环境，在 Windows、 Mac 和 Linux 系统上运行。 在 Microsoft [C /C++用于 Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)扩展插件支持 IntelliSense、 调试、 代码格式设置、 自动完成功能。 Visual Studio for Mac 不支持 Microsoft C++，但.NET 语言和跨平台开发支持。 有关安装说明，请参阅[安装 Visual Studio for Mac](/visualstudio/mac/installation/)。

想要详细了解此版本的其他新增功能？ 请参阅 Visual Studio[发行说明](/visualstudio/releases/2019/release-notes/)。

准备安装？ 我们将逐步引导你完成安装。

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>第 1 步 - 确保计算机支持 Visual Studio

开始安装 Visual Studio 前：

1. 查看[系统要求](/visualstudio/releases/2019/system-requirements)。 这些要求有助于了解计算机是否支持 Visual Studio 2019。

1. 应用最新的 Windows 更新。 这些更新可确保计算机包含最新的安全更新程序和 Visual Studio 所需的系统组件。

1. 重新启动。 重新启动可确保挂起的任何安装或更新都不会影响 Visual Studio 安装。

1. 释放空间。 通过运行磁盘清理应用程序等方式，从 %SystemDrive% 删除不需要的文件和应用程序。

有关使用 Visual Studio 2019 运行以前版本的 Visual Studio 并行问题，请参阅[Visual Studio 2019 平台目标以及兼容性](/visualstudio/releases/2019/compatibility/)页。

### <a name="step-2---download-visual-studio"></a>第 2 步 - 下载 Visual Studio

接下来，下载 Visual Studio 引导程序文件。 为此，请选择下面的按钮，选择你想选择的 Visual studio 的版本**保存**，然后选择**打开文件夹**。

 > [!div class="button"]
 > [下载 Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>第 3 步 - 卸载 Visual Studio 安装程序

运行引导程序文件以安装 Visual Studio 安装程序。 这个新的轻型安装程序包括来安装和自定义 Visual Studio 所需的一切。

1. 在“下载”文件夹中，双击与下列文件之一匹配或类似的引导程序文件：

   * 对于 Visual Studio Community，请运行 **vs_community.exe**
   * 对于 Visual Studio Professional，请运行 **vs_professional.exe**
   * 对于 Visual Studio Enterprise，请运行 **vs_enterprise.exe**

   如果收到用户帐户控制通知，请选择**是**。

1. 我们会要求确认 Microsoft [许可条款](https://visualstudio.microsoft.com/license-terms/)和 Microsoft [隐私声明](https://privacy.microsoft.com/privacystatement)。 选择**继续**。

### <a name="step-4---choose-workloads"></a>步骤 4-选择工作负荷

安装程序安装后，可以使用它通过选择自定义安装*工作负荷*，或功能集，所需。 操作方法如下。

1. 在“安装 Visual Studio”屏幕中找到所需的工作负载。

   ![Visual Studio 2019：安装工作负荷](../get-started/media/vs-installer-workloads.png)

   Core 的C++支持中，选择"使用的桌面开发C++"工作负荷。 它附带默认核心编辑器，该编辑器针对超过 20 种语言提供基本代码编辑支持，能够打开和编辑任意文件夹中的代码（而无需使用项目），还提供集成的源代码管理。

   其他工作负荷都支持其他类型的C++开发。 例如，选择要创建 Windows 运行时使用的 Microsoft Store 应用的"通用 Windows 平台开发"工作负荷。 选择"游戏开发使用C++"创建使用 DirectX、 Unreal 和 Cocos2d 的游戏。 选择"使用的 Linux 开发C++"到目标 Linux 平台，包括 IoT 开发。

   **安装详细信息**窗格列出了安装每个工作负荷的包含和可选组件。 您可以选择或取消选择此列表中的可选组件。 例如，若要支持开发使用 Visual Studio 2017 或 2015年编译器工具集，选择 MSVC v141 或 MSVC v140 可选组件。 可以添加对 MFC、 实验性模块语言扩展、 IncrediBuild，和的详细信息的支持。

1. 选择工作负载和所需的可选组件后，请选择**安装**。

    接下来，会出现多个显示 Visual Studio 安装进度的状态屏幕。

> [!TIP]
> 在安装之后，可以随时安装最初未安装的工作负荷或组件。 如果已打开 Visual Studio，请转到“工具” > “获取工具和功能...”，这会打开 Visual Studio 安装程序。 或者，从“开始”菜单打开“Visual Studio 安装程序”。 在这里，可以选择的工作负荷或你想要安装的组件。 然后，选择**修改**。

## <a name="step-5---choose-individual-components-optional"></a>步骤 5-选择各个组件 （可选）

如果不想要使用的工作负载功能来自定义 Visual Studio 安装，或者想要添加更多组件不是工作负载安装，就可以做到安装或添加各个组件从**各个组件**选项卡。选择你想要，然后按照提示进行操作。

  ![Visual Studio 2019-安装各个组件](../get-started/media/vs-installer-individual-components.png "安装 Visual Studio 各个组件")

## <a name="step-6---install-language-packs-optional"></a>第 6 步 - 安装语言包（可选）

默认情况下，安装程序首次运行时会尝试匹配操作系统语言。 若要在所选的语言安装 Visual Studio，选择**语言包**从 Visual Studio 安装程序，选项卡，然后按照提示进行操作。

  ![Visual Studio 2019-安装语言包](../get-started/media/vs-installer-language-packs.png "安装 Visual Studio 语言包")

### <a name="change-the-installer-language-from-the-command-line"></a>从命令行更改安装程序语言

更改默认语言的另一种方法是从命令行运行安装程序。 例如，可以通过运行以下命令来强制安装程序用英语运行：`vs_installer.exe --locale en-US`。 在下一次运行时，安装程序将记住此设置。 安装程序支持以下语言标记：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

### <a name="step-7---change-the-installation-location-optional"></a>第 7 步 - 更改安装位置（可选）

系统驱动器上，可以减少 Visual Studio 的安装空间占用量。 可以选择将下载缓存、共享组件、SDK 和工具移动到不同驱动器，并将 Visual Studio 安装在其运行速度最快的驱动器上。

  ![Visual Studio 2019-更改安装位置](../get-started/media/vs-installer-installation-locations.png "更改安装位置")

> [!IMPORTANT]
> 仅当首次安装 Visual Studio 时，可以选择一个不同的驱动器。 如果你已安装它，并想要更改驱动器，必须卸载 Visual Studio，然后重新安装它。

## <a name="step-8---start-developing"></a>第 8 步 - 开始开发

1. Visual Studio 安装完成后，选择**启动**按钮以开始使用 Visual Studio 进行开发。

1. 在“开始”窗口上，选择“创建新项目”。

1. 在搜索框中，输入你想要创建以查看可用模板列表的应用程序的类型。 模板列表取决于在安装期间选择的工作负载。 若要查看不同的模板，请选择不同的工作负荷。

   此外可以通过筛选特定编程语言搜索**语言**下拉列表。 可以使用筛选**平台**列表和**项目类型**列出，请过。

1. Visual Studio 会打开新的项目，然后便可以对代码 ！

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安装

在 Visual Studio 2017 中，很容易选择并安装所需的功能。 并且由于其降低的最小内存需求量，安装速度快、 系统影响更小。

### <a name="prerequisites"></a>系统必备

- 宽带 Internet 连接。 Visual Studio 安装程序可以下载几千兆字节的数据。

- 运行 Microsoft Windows 7 或更高版本的计算机。 建议使用 Windows 10 以获得最佳开发体验。 安装 Visual Studio 前，请确保向系统应用最新更新。

- 足够的可用磁盘空间。 Visual Studio 需要至少为 7 GB 的磁盘空间，可能需要 50 GB 或更多如果安装了许多常见选项。 建议将其安装在 C: 驱动器上。

有关磁盘空间和操作系统要求的详细信息，请参阅 [Visual Studio 产品系列系统要求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安装程序会报告所选选项需要多少磁盘空间。

### <a name="download-and-install"></a>下载并安装

1. 下载 Windows 的最新 Visual Studio 2017 安装程序。

   > [!div class="nextstepaction"]
   > [安装 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 适用于个体开发者、课堂学习、学术研究和开放源代码开发。 对于其他用途，请安装 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 找到你下载的安装程序文件并运行。 它可能会在浏览器中显示，或者，可以在“下载”文件夹中找到它。 安装程序需要管理员权限才能运行。 可能会看到**用户帐户控制**对话框，要求授予安装程序对系统进行更改的权限; 请选择**是**。 如果遇到问题，在文件资源管理器中查找下载的文件、 右键单击该安装程序图标，并选择**以管理员身份运行**从上下文菜单。

   ![下载并安装 Visual Studio 安装程序](media/vscpp-concierge-run-installer.gif "下载并安装 Visual Studio 安装程序")

1. 安装程序会向显示工作负荷列表，这些工作负荷是特定开发区域的相关选项组。 现在，对 C++ 的支持是可选工作负荷（默认情况下不会安装）的一部分。

   ![使用的桌面开发C++工作负荷](media/desktop-development-with-cpp.png "使用的桌面开发C++")

   有关C++，选择**使用的桌面开发C++** 工作负荷，然后选择**安装**。

   ![安装使用的桌面开发C++工作负荷](media/vscpp-concierge-choose-workload.gif "安装使用的桌面开发C++工作负荷")

1. 安装完成后，选择**启动**按钮以启动 Visual Studio。

   首次运行 Visual Studio 中，您需要使用 Microsoft 帐户登录。 如果没有此类帐户，则可以免费创建一个。 还必须选择一个主题。 别担心，后期可以根据需要进行更改。

   第一次运行时，Visual Studio 可能需要几分钟才能使用。 下面是快速延时的演示：

   ![在登录 visual Studio 2017](media/vscpp-quickstart-first-run.gif "登录 Visual Studio 2017")

   再次运行时，visual Studio 的启动速度快得多。

1. Visual Studio 打开时，检查标题栏中的标志图标是否突出显示：

   ![Visual Studio 2017 通知标志](media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知标志")

   如果突出显示，选择它以打开**通知**窗口。 如果有任何适用于 Visual Studio 的更新，建议立即安装。 安装完成后，请重启 Visual Studio。

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安装

若要安装 Visual Studio 2015，请转到[下载较旧版本的 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 运行安装程序并选择**自定义安装**，然后选择 C++ 组件。 要向现有 Visual Studio 2015 安装添加 C++ 支持，请单击 Windows 开始按钮，然后键入**添加或删除程序**。 从结果列表中打开该程序，然后在已安装的程序列表中找到你的 Visual Studio 2015 安装。 双击它，然后选择**修改**并选择要安装的 Visual C++ 组件。

通常，即使需要使用 Visual Studio 2015 编译器编译代码，我们仍强烈建议使用 Visual Studio 2017。 有关更多信息，请参阅[使用 Visual Studio 中的本机多重目标生成旧项目](../porting/use-native-multi-targeting.md)。

::: moniker-end

当运行 Visual Studio 时，你准备好继续下一步。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [创建C++项目](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />

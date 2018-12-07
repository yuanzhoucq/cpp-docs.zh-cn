---
title: 在 Visual Studio 2017 中安装 c + + 支持
description: 安装 Visual c + + 的 Visual Studio 支持
ms.custom: mvc
ms.date: 11/19/2018
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: ac8439e1709b6bbce6f32580bafee50c9ff30e3f
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977740"
---
# <a name="install-c-support-in-visual-studio"></a>在 Visual Studio 中安装 c + + 支持

如果尚未下载，并且尚未安装 Visual Studio 2017 和 Visual c + + 工具，下面介绍了如何开始。

## <a name="prerequisites"></a>系统必备

- 宽带 internet 连接。 在 Visual Studio 安装程序可以下载数千兆字节的数据。

- 运行 Microsoft Windows 7 或更高版本的计算机。 我们建议获取最佳开发体验的 Windows 10。 请确保先安装 Visual Studio 最新的更新应用于您的系统。

- 足够的可用磁盘空间。 Visual Studio 需要至少为 7 GB 的磁盘空间，可能需要 50 GB 或更多如果安装了许多常见选项。 我们建议将其安装在 c： 驱动器。

有关磁盘空间和操作系统要求的详细信息，请参阅[Visual Studio 产品系列系统要求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安装程序报告磁盘空间量是需要您选择的选项。

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安装

若要安装 Visual Studio 2015，请转到[下载较旧版本的 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 运行安装程序并选择“自定义安装”，然后选择 C++ 组件。 若要将 c + + 支持添加到现有 Visual Studio 2015 安装，单击 Windows 开始按钮并键入**添加或删除程序**。 从结果列表中打开的程序，然后在已安装的程序列表中找到 Visual Studio 2015 安装。 双击它，然后选择**修改**，然后选择要安装的 Visual c + + 组件。

一般情况下，强烈建议使用 Visual Studio 2017，即使需要使用 Visual Studio 2015 编译器编译代码。 有关详细信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](../porting/use-native-multi-targeting.md)。

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安装

1. 下载 Windows 的最新 Visual Studio 2017 安装程序。

   > [!div class="nextstepaction"]
   > [安装 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 适用于个体开发者、课堂学习、学术研究和开放源代码开发。 对于其他用途，请安装 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 找到你下载并运行它的安装程序文件。 它可能会显示在浏览器中，或在 Downloads 文件夹中可能会发现。 安装程序需要管理员特权才能运行。 你可能会看到**用户帐户控制**对话框，要求将由安装程序对您的系统进行更改; 选择权限授予**是**。 如果遇到问题，在文件资源管理器中查找下载的文件、 右键单击该安装程序图标，并选择**以管理员身份运行**从上下文菜单。

   ![下载并安装 Visual Studio 安装程序](../build/media/vscpp-concierge-run-installer.gif "下载并安装 Visual Studio 安装程序")

1. 安装程序提供工作负载列表，即一组用于特定开发领域的相关选项。 对 c + + 支持现在是默认情况下不安装的可选工作负荷的一部分。

   ![使用 c + + 工作负荷的桌面开发](../build/media/desktop-development-with-cpp.png "使用 c + + 的桌面开发")

   对于 c + +，请选择**使用 c + + 的桌面开发**工作负荷，然后选择**安装**。

   ![安装使用 c + + 工作负荷的桌面开发](../build/media/vscpp-concierge-choose-workload.gif "安装使用 c + + 工作负荷的桌面开发")

1. 安装完成后，选择**启动**按钮以启动 Visual Studio。

   首次运行 Visual Studio 中，需要使用 Microsoft 帐户登录。 如果你没有帐户，则可以免费创建一个。 此外必须选择一个主题。 别担心，可以在如果要以后更改。

   它可能需要 Visual Studio 几分钟时间才能使可供使用首次运行它。 下面是如下所示在慢镜头快速：

   ![在登录 visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "登录 Visual Studio 2017")

   再次运行时，visual Studio 的启动速度快得多。

1. Visual Studio 打开时，请检查将突出显示的标题栏中的标记图标：

   ![Visual Studio 2017 通知标志](../build/media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知标志")

   如果突出显示，选择它以打开**通知**窗口。 如果有任何更新提供适用于 Visual Studio，我们建议立即安装。 安装完成后，重新启动 Visual Studio。

当运行 Visual Studio 时，已准备好继续下一步。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [创建 c + + 项目](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />

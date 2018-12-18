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

- 宽带互联网连接。 Visual Studio 安装程序可以下载几千兆字节的数据。

- 运行 Microsoft Windows 7 或更高版本的计算机。 我们建议使用 Windows 10 以获得最佳开发体验。 在安装 Visual Studio 之前，请确保将最新更新应用于您的系统。

- 足够的可用磁盘空间。 Visual Studio 需要至少7GB的磁盘空间，如果安装了许多常用选项，则可能需要50GB或更多。 我们建议您将其安装在C盘上。

有关磁盘空间和操作系统要求的详细信息，请参阅[Visual Studio 产品系列系统要求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安装程序会报告您选择的选项需要多少磁盘空间。

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安装

若要安装 Visual Studio 2015，请转到[下载较旧版本的 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 运行安装程序并选择“自定义安装”，然后选择 C++ 组件。 要向现有 Visual Studio 2015 安装添加 C++ 支持，请单击 Windows 开始按钮，然后键入**添加或删除程序**。 从结果列表中打开该程序，然后在已安装的程序列表中找到您的 Visual Studio 2015 安装。 双击它，然后选择**修改**并选择要安装的 Visual C++ 组件。

通常，我们强烈建议您使用 Visual Studio 2017，即使您需要使用 Visual Studio 2015 编译器编译代码。 有关更多信息，请参阅 [使用 Visual Studio 中的本机多重目标生成旧项目](../porting/use-native-multi-targeting.md)。

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安装

1. 下载 Windows 的最新 Visual Studio 2017 安装程序。

   > [!div class="nextstepaction"]
   > [安装 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 适用于个体开发者、课堂学习、学术研究和开放源代码开发。 对于其他用途，请安装 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 找到您下载的安装程序文件并运行它。 它可能会显示在您的浏览器中，或者您可以在“下载”文件夹中找到它。 安装程序需要管理员权限才能运行。 您可能会看到**用户帐户控制**对话框，要求您授予安装程序对系统进行更改的权限; 选择**是**。 如果遇到问题，请在文件资源管理器中找到下载的文件，右键单击安装程序图标，然后从上下文菜单中选择**以管理员身份运行**。


   ![下载并安装 Visual Studio 安装程序](../build/media/vscpp-concierge-run-installer.gif "下载并安装 Visual Studio 安装程序")

1. 安装程序会向您显示工作负载列表，这些工作负载是特定开发区域的相关选项组。 现在，对 C++ 的支持是可选工作负载的一部分，默认情况下不会安装。

   ![使用 c + + 工作负荷的桌面开发](../build/media/desktop-development-with-cpp.png "使用 c + + 的桌面开发")

   对于 c + +，请选择**使用 c + + 的桌面开发**工作负荷，然后选择**安装**。

   ![安装使用 c + + 工作负荷的桌面开发](../build/media/vscpp-concierge-choose-workload.gif "安装使用 c + + 工作负荷的桌面开发")

1. 安装完成后，选择**启动**按钮以启动 Visual Studio。

   第一次运行Visual Studio时，系统会要求您使用Microsoft帐户登录。 如果您没有，可以免费创建一个。 您还必须选择一个主题。 别担心，如果您愿意，可以稍后更改。

   Visual Studio 可能需要几分钟才能在第一次运行时使用。 这是快速延时的样子：

   ![在登录 visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "登录 Visual Studio 2017")

   再次运行时，visual Studio 的启动速度快得多。

1. Visual Studio打开时，检查标题栏中的标志图标是否高亮显示：

   ![Visual Studio 2017 通知标志](../build/media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知标志")

   如果高亮显示，选择它以打开**通知**窗口。 如果有任何更新提供适用于 Visual Studio，我们建议立即安装。 安装完成后，重新启动 Visual Studio。

当运行 Visual Studio 时，已准备好继续下一步。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [创建 c + + 项目](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />

---
title: Visual Studio 中安装 c + + 支持 |Microsoft 文档
description: 安装 Visual c + + 的 Visual Studio 支持
ms.custom: mvc
ms.date: 06/21/2018
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5807110caf730c72d93de7e1265199b63f1d6bff
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322480"
---
# <a name="install-c-support-in-visual-studio"></a>Visual Studio 中安装 c + + 支持

如果你尚未下载，并且尚未安装 Visual Studio 和 Visual c + + 工具，下面介绍了如何开始。

## <a name="prerequisites"></a>系统必备

- 宽带 internet 连接。 Visual Studio 安装程序可以下载数据达到数千兆的字节。

- 运行 Microsoft Windows 7 或更高版本的计算机。 为获得最佳的开发体验，我们建议 Windows 10。 请确保在安装 Visual Studio 之前，将最新的更新应用到你的系统。

- 足够的可用磁盘空间。 Visual Studio 需要至少 7 GB 的磁盘空间，而且可能需要 50 GB 或更高如果安装了许多常用的选项。 我们建议将其安装在 c： 驱动器。

有关磁盘空间和操作系统要求的详细信息，请参阅[Visual Studio 产品系列系统要求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安装报告多少磁盘空间，才能使用你选择的选项。

## <a name="installation"></a>安装

1. 下载适用于 Windows 最新的 Visual Studio 2017 安装程序。

   > [!div class="nextstepaction"]
   > <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">安装 Visual Studio 2017 Community</a>

   >[!Tip]
   > Community Edition 适用于个体开发者、课堂学习、学术研究和开放源代码开发。 对于其他用途，请安装 <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Visual Studio 2017 Professional</a> 或 <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Visual Studio 2017 Enterprise</a>。

1. 查找安装程序文件下载并运行它。 它可能会显示在浏览器中，或可能在 Downloads 文件夹中找到它。 安装程序需要管理员特权才能运行。 你可能会看到**用户帐户控制**对话框，要求您为授予权限以便安装到你的系统进行更改; 选择**是**。 如果你遇到的问题，在文件资源管理器中查找下载的文件、 右键单击该安装程序图标，并选择**以管理员身份运行**从上下文菜单。

   ![运行 Visual Studio 2017 安装程序](../build/media/vscpp-concierge-run-installer.gif "运行 Visual Studio 安装程序")

1. 安装程序提供工作负载列表，即一组用于特定开发领域的相关选项。 对 c + + 支持现在是默认情况下不安装的可选工作负载的一部分。

   ![使用 c + + 桌面开发](../build/media/desktop-development-with-cpp.png "使用 c + + 桌面开发")

    对于 c + + 中，选择**使用 c + + 桌面开发**工作负荷，然后选择**安装**。

   ![情况下安装桌面开发的 c + + 工作负荷](../build/media/vscpp-concierge-choose-workload.gif "情况下安装桌面开发的 c + + 工作负荷")

1. 当安装完成后时，选择**启动**按钮以启动 Visual Studio。

   首次运行 Visual Studio 中，需要使用 Microsoft 帐户登录。 如果你没有帐户，你可以免费创建一个。 你还必须选择一个主题。 别担心，可以在如果要以后更改。 

   它可能需要 Visual Studio 几分钟到以使可供使用第一次你运行它。 下面是如下所示在定时快速中：

   ![Visual Studio 2017 登录](../build/media/vscpp-quickstart-first-run.gif "Visual Studio 2017 登录")

   当你再次运行时，visual Studio 的启动速度快得多。

1. 当 Visual Studio 打开时，请检查是否突出显示的标题栏中的标志图标：

   ![Visual Studio 2017 通知标志](../build/media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知标志")

   如果突出显示它时，选择它以打开**通知**窗口。 如果有适用于 Visual Studio 的任何更新，我们建议立即安装。 安装完成后，重新启动 Visual Studio。

当运行 Visual Studio 时，你就可以继续下一步。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [创建 c + + 项目](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />

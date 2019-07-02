---
title: 演练：部署程序 (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: 5cc4ead7aaef2ffa56870a374b0b73d16eb31521
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400959"
---
# <a name="walkthrough-deploying-your-program-c"></a>演练：部署程序 (C++)

现在已通过完成早期相关演练创建了应用程序，最后一步是创建安装程序以便其他用户将程序安装到自己的计算机上。 对于安装程序，你需要将新项目添加到现有解决方案。 此新项目输出 setup.exe 文件，该文件将把你的应用程序安装到其他计算机上。

本演练演示如何使用 Windows Installer 部署应用程序。 你还可以使用 ClickOnce 部署应用程序。 有关详细信息，请参阅[Visual c + + 应用程序的 ClickOnce 部署](../windows/clickonce-deployment-for-visual-cpp-applications.md)。 有关一般部署的详细信息，请参阅[部署应用程序、服务和组件](/visualstudio/deployment/deploying-applications-services-and-components)。

## <a name="prerequisites"></a>系统必备

- 本演练假定你具备 C++ 语言的基础知识。

- 它还假定你已完成之前在[使用 Visual Studio IDE 进行 C++ 桌面开发](using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的相关演练。

- 本演练无法在 Visual Studio 速成版中完成。

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>安装 Visual Studio 安装程序并部署项目模板

本部分中的步骤因安装的 Visual Studio 版本而异。 确保本页左上角的版本选择器已正确设置。

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>安装 Visual Studio 2019 安装程序并部署项目模板

1. 如果尚未执行此操作，请下载 Microsoft Visual Studio 安装程序项目扩展。 此扩展可供 Visual Studio 开发人员免费使用，并向 Visual Studio 添加安装和部署项目模板功能。 连接到 Internet 后，在 Visual Studio 中选择“扩展” > “管理扩展”   。 在“扩展和更新”  对话框下，选择“联机”  选项卡并在搜索框中键入“Microsoft Visual Studio 安装程序项目”  。 点击 Enter  ，选择”Microsoft Visual Studio”\<“版本”>”安装程序项目”  ，然后单击“下载”  。 选择运行并安装扩展，然后重新启动 Visual Studio。

1. 在 Visual Studio 菜单栏上，选择“文件”>“最近使用的项目和解决方案”，然后选择重新打开项目   。

1. 在菜单栏上，选择“文件” > “新建” > “项目”，打开“创建新项目”对话框     。 在搜索框中，键入“设置”，然后从结果列表中选择“设置项目”  。

1. 在“名称”框中输入安装项目的名称  。 在“解决方案”下拉列表中，选择“添加到解决方案”   。 选择“确定”按钮，创建安装项目  。 在编辑器窗口中打开“文件助手(ProjectName)”  选项卡。

1. 右键单击“应用程序文件夹”节点，然后选择“添加”>“项目输出”以打开“添加项目输出组”对话框     。

1. 在对话框中，选择“主输出”  ，然后单击“确定”  。 将出现名为“游戏(活动)主输出”  的新项。

1. 选择项“游戏(活动)主输出”  ，右键单击并选择“创建游戏(活动)主输出的快捷方式”  。 将出现名为“游戏(活动)主输出的快捷方式”  的新项。

1. 将快捷方式项重命名为“游戏”  ，然后将项拖放到窗口左侧的“用户程序菜单”  节点。

1. 在“解决方案资源管理器”中，选择“游戏安装程序”项目，然后选择“视图”>“属性窗口”或点击 **F4** 以打开“属性”窗口      。

1. 指定希望它们显示在安装程序中，则指定其他详细信息。  例如，为“制造商”使用“Contoso”，为“产品名称”使用“游戏安装程序”，并为“SupportUrl”使用 http\://www.contoso.com       。

1. 在菜单栏上，依次选择“生成” > “Configuration Manager”   。 在“项目”  表的“生成”  列下，勾选“游戏安装程序”  框。 单击 **“关闭”** 。

1. 在菜单栏上，选择“生成”>“生成解决方案”，以生成“游戏”项目和“游戏安装程序”项目   。

1. 在解决方案文件夹中，找到从游戏安装程序项目生成的 setup.exe 程序，然后运行该程序将游戏应用程序安装到计算机上。 可在另一台计算机上复制此文件（和 GameInstaller.msi），来安装应用程序及其所需的库文件。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>安装 Visual Studio 2017 及更低版本安装程序并部署项目模板

1. 连接到 Internet 后，在 Visual Studio 中选择“工具”>“扩展和更新”   。

1. 在“扩展和更新”  下，选择“联机”  选项卡并在搜索框中键入“Microsoft Visual Studio 安装程序项目”  。 点击 Enter  ，选择”Microsoft Visual Studio”\<“版本”>”安装程序项目”  ，然后单击“下载”  。

1. 选择安装扩展，然后重新启动 Visual Studio。

1. 在菜单栏上，选择“文件”>“最近使用的项目和解决方案”，然后选择“游戏”解决方案以将其重新打开    。

### <a name="to-create-a-setup-project-and-install-your-program"></a>创建安装项目和安装程序

1. 将活动解决方案配置更改为“发布”。 在菜单栏上，依次选择“生成” > “Configuration Manager”   。 从“Configuration Manager”对话框的“活动解决方案配置”下拉列表中选择“发布”    。 选择“关闭”按钮，保存配置  。

1. 在菜单栏上，选择“文件”>“新建”>“项目”，打开“新建项目”对话框     。

1. 在对话框的左窗格中，依次展开“已安装应用程序”   > “其他项目类型”  节点，然后选择“Visual Studio 安装程序”  。 在中间窗格中，选择“安装项目”  。

1. 在“名称”框中输入安装项目的名称  。 对于此示例，请输入“游戏安装程序”  。 在“解决方案”下拉列表中，选择“添加到解决方案”   。 选择“确定”按钮，创建安装项目  。 在编辑器窗口中打开“文件助手(游戏安装程序)”  选项卡。

1. 右键单击“应用程序文件夹”节点，然后选择“添加”>“项目输出”以打开“添加项目输出组”对话框     。

1. 在对话框中，选择“主输出”  ，然后单击“确定”  。 将出现名为“游戏(活动)主输出”  的新项。

1. 选择项“游戏(活动)主输出”  ，右键单击并选择“创建游戏(活动)主输出的快捷方式”  。 将出现名为“游戏(活动)主输出的快捷方式”  的新项。

1. 将快捷方式项重命名为“游戏”  ，然后将项拖放到窗口左侧的“用户程序菜单”  节点。

1. 在“解决方案资源管理器”中，选择“游戏安装程序”项目，然后选择“视图”>“属性窗口”或点击 **F4** 以打开“属性”窗口      。

1. 指定希望它们显示在安装程序中，则指定其他详细信息。  例如，为“制造商”使用“Contoso”，为“产品名称”使用“游戏安装程序”，并为“SupportUrl”使用 http\://www.contoso.com       。

1. 在菜单栏上，依次选择“生成” > “Configuration Manager”   。 在“项目”  表的“生成”  列下，勾选“游戏安装程序”  框。 单击 **“关闭”** 。

1. 在菜单栏上，选择“生成”>“生成解决方案”，以生成“游戏”项目和“游戏安装程序”项目   。

1. 在解决方案文件夹中，找到从游戏安装程序项目生成的 setup.exe 程序，然后运行该程序将游戏应用程序安装到计算机上。 可在另一台计算机上复制此文件（和 GameInstaller.msi），来安装应用程序及其所需的库文件。

::: moniker-end

## <a name="next-steps"></a>后续步骤

上一步：  [演练：调试项目 (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](../build/projects-and-build-systems-cpp.md)<br/>
[部署桌面应用程序](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>

---
title: 演练：部署程序 (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1753c63673b9dd083e2b690788801bd467938c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335531"
---
# <a name="walkthrough-deploying-your-program-c"></a>演练：部署程序 (C++)
现在已通过完成先前相关演练创建了应用程序，该演练在[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出，最后一步是创建安装程序以便其他用户将程序安装到其计算机上。 为此，你需要将新项目添加到现有解决方案。 此新项目输出 setup.exe 文件，该文件将把你的应用程序安装到其他计算机上。  
  
 本演练演示如何使用 Windows Installer 部署应用程序。 你还可以使用 ClickOnce 部署应用程序。 有关详细信息，请参阅 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。 有关一般部署的详细信息，请参阅[部署应用程序、服务和组件](/visualstudio/deployment/deploying-applications-services-and-components)。  
  
## <a name="prerequisites"></a>系统必备  
  
-   本演练假定你具备 C++ 语言的基础知识。  
  
-   它还假定你已完成之前在[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)中列出的相关演练。  
  
-   本演练无法在 Visual Studio Express 版中完成。  
  
-   如果你尚未完成上述演练，则如本文后续步骤所述，下载 InstallShield limited Edition (ISLE)。 ISLE 可供 Visual Studio 开发人员免费使用，它取代了 Visual Studio 早期版本中的安装和部署项目模板功能。  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>安装 ISLE 安装和部署项目模板  
  
1.  连接到 Internet 后，在菜单栏上依次选择“文件”、“新建”、“项目”，打开“新建项目”对话框。  
  
2.  在对话框的左窗格中，依次展开“已安装应用程序”、“模板”和“其他项目类型”节点，然后选择“安装和部署”。 在中间窗格中，选择“启用 InstallShield Limited Edition”，然后选择“确定”按钮。  
  
3.  遵照说明安装 InstallShield Limited Edition for Visual Studio (ISLE)。  
  
4.  在你下载、安装并激活 ISLE 后，请关闭 Visual Studio，然后重新打开。  
  
5.  在菜单栏上，依次选择“文件”、“最近使用的项目和解决方案”，然后选择“游戏”解决方案重新打开。  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>创建安装项目和安装程序  
  
1.  将活动解决方案配置更改为“发布”。 在菜单栏上，依次选择 **“生成”**、 **“配置管理器”**。 从“Configuration Manager”对话框的“活动解决方案配置”下拉列表中选择“发布”。 选择“关闭”按钮，保存配置。  
  
2.  在菜单栏上，依次选择“文件”、“新建”、“项目”，打开“新建项目”对话框。  
  
3.  在对话框的左窗格中，依次展开“已安装应用程序”、“模板”和“其他项目类型”节点，然后选择“安装和部署”。 在中间窗格中，选择“InstallShield limited Edition 项目”。  
  
4.  在“名称”框中输入安装项目的名称。 对于此示例，请输入“游戏安装程序”。 在“解决方案”下拉列表中，选择“添加到解决方案”。 选择“确定”按钮，创建安装项目。 在编辑器窗口中打开“项目助手(游戏安装程序)”选项卡。  
  
5.  在“项目助手(游戏安装程序)”选项卡底部，选择“应用程序信息”链接。  
  
6.  在“应用程序信息”页上，如果希望公司名称显示在安装程序中，请指定公司名称。 可以使用自己的公司名称，或者在此示例中使用 Contoso 作为公司名称。 指定应用程序名称；在该示例中，指定“游戏”。 指定公司 Web 地址，或者在该示例中，使用 http://www.contoso.com。  
  
7.  在“项目助手(游戏安装程序)”选项卡底部，选择“安装访谈”链接。  
  
8.  在“安装访谈”页上，在“是否显示许可协议对话框”下，选择“否”选项按钮。 在“是否提示用户输入其公司名称和用户名”下，选择“否”选项按钮。  
  
9. 在“解决方案资源管理器”中，依次展开“游戏安装程序”项目、“组织安装”节点，然后打开“常规信息”页。  
  
10. 在编辑器窗口的“一般信息(游戏安装程序)”选项卡中，指定“标记创建者 ID”，例如，regid.2012-12.com.Contoso。  
  
11. 在“解决方案资源管理器”中，在“游戏安装程序”项目下，展开“指定应用程序数据”节点，然后打开“文件”页。  
  
12. 在编辑器窗口的“文件(游戏安装程序)”选项卡中，在“源计算机文件”下，打开“游戏的主输出”快捷菜单，然后选择“复制”。  
  
13. 在“目标计算机文件”的“名称”列下的空白处打开快捷菜单，然后选择“粘贴”。 屏幕上将显示名为“Game.Primary Output”的新项。  
  
14. 在“解决方案资源管理器”中，在“指定应用程序数据”节点下，打开“可再发行组件”页。  
  
15. 在编辑器窗口中“可再发行组件(游戏安装程序)”选项卡中，选中“Visual C++ 11.0 CRT (x86)”复选框。  
  
16. 在菜单栏上，依次选择“生成”、“生成解决方案”，生成游戏项目和游戏安装程序项目。  
  
17. 在解决方案文件夹中，找到从游戏安装程序项目生成的 setup.exe 程序，然后运行该程序将游戏应用程序安装到计算机上。 可在另一台计算机上复制此文件，来安装应用程序及其所需的库文件。  
  
18. 可以在安装项目中设置多个选项，满足你的需求。 有关更多信息，请在“游戏安装程序”项目下的“解决方案资源管理器”中打开“入门”页，然后选择 F1 键打开 ISLE Help Library。  
  
## <a name="next-steps"></a>后续步骤  
 **上一步：**[演练：调试项目 (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
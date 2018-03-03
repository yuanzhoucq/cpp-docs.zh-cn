---
title: "演练： 部署程序 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce59dc7b767c8ff8e988ac7a765d3bb5f1cdfffc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-your-program-c"></a>演练：部署程序 (C++)
现在，你已创建你的应用程序通过完成前面相关的演练中，列出了这些[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)，最后一步是，以便其他用户可以创建安装程序在其计算机上安装的程序。 为此，你需要将新项目添加到现有解决方案。 此新项目输出 setup.exe 文件，该文件将把你的应用程序安装到其他计算机上。  
  
 本演练演示如何使用 Windows Installer 部署应用程序。 你还可以使用 ClickOnce 部署应用程序。 有关详细信息，请参阅 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。 有关部署的详细信息一般情况下，请参阅[部署应用程序、 服务和组件](/visualstudio/deployment/deploying-applications-services-and-components)。  
  
## <a name="prerequisites"></a>系统必备  
  
-   本演练假定你具备 C++ 语言的基础知识。  
  
-   它还假定你已完成中列出的更早版本相关的演练[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
-   本演练无法在 Visual Studio Express 版中完成。  
  
-   如果你尚未完成上述演练，则如本文后续步骤所述，下载 InstallShield limited Edition (ISLE)。 ISLE 可供 Visual Studio 开发人员免费使用，它取代了 Visual Studio 早期版本中的安装和部署项目模板功能。  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>安装 ISLE 安装和部署项目模板  
  
1.  当您连接到 Internet，在菜单栏上，选择**文件**，**新建**，**项目**以打开**新项目**对话框。  
  
2.  在对话框中的左窗格中，展开**已安装**，**模板**，和**其他项目类型**节点，然后选择**安装和部署**. 在中心窗格中，选择**启用 InstallShield Limited Edition** ，然后选择**确定**按钮。  
  
3.  遵照说明安装 InstallShield Limited Edition for Visual Studio (ISLE)。  
  
4.  在你下载、安装并激活 ISLE 后，请关闭 Visual Studio，然后重新打开。  
  
5.  在菜单栏上，选择**文件**，**最近使用的项目和解决方案**，然后选择**游戏**解决方案可重新打开它。  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>创建安装项目和安装程序  
  
1.  将活动解决方案配置更改为“发布”。 在菜单栏上，依次选择 **“生成”**、 **“配置管理器”**。 在**Configuration Manager**对话框中，在**活动解决方案配置**下拉列表中，选择**版本**。 选择**关闭**按钮以保存配置。  
  
2.  在菜单栏上，选择**文件**，**新建**，**项目**以打开**新项目**对话框。  
  
3.  在对话框中的左窗格中，展开**已安装**，**模板**，和**其他项目类型**节点，然后选择**安装和部署**. 在中心窗格中，选择**InstallShield Limited Edition 项目**。  
  
4.  输入中的安装项目的名称**名称**框。 对于此示例中，输入**游戏安装程序**。 在**解决方案**下拉列表中，选择**将添加到解决方案**。 选择**确定**按钮以创建安装项目。 A**项目助手 （游戏安装程序）**选项卡将在编辑器窗口中打开。  
  
5.  在底部**项目助手 （游戏安装程序）**选项卡上，选择**应用程序信息**链接。  
  
6.  上**应用程序信息**页上，指定你的公司名称，如你希望其出现在安装程序。 你可以使用你自己的公司名称，或对于此示例中，使用**Contoso**。 指定你的应用程序名称;在此示例中，指定**游戏**。 指定你公司的 web 地址，或对于此示例中，使用**http://www.contoso.com**。  
  
7.  在底部**项目助手 （游戏安装程序）**选项卡上，选择**安装访谈**链接。  
  
8.  上**安装访谈**页上，在**你想要显示许可协议对话框**，选择**否**选项按钮。 下**你想要提示用户输入其公司名称和用户名**，选择**否**选项按钮。  
  
9. 在**解决方案资源管理器**，展开**游戏安装程序**项目中，展开**组织你的安装**节点，然后打开**的一般信息**页。  
  
10. 上**常规信息 （游戏安装程序）**在编辑器窗口中的选项卡上，指定**标记创建者 ID**，例如， **regid.2012-12.com.contoso**。  
  
11. 在**解决方案资源管理器**下**游戏安装程序**项目中，展开**指定应用程序数据**节点，然后打开**文件**页。  
  
12. 上**文件 （游戏安装程序）**选项卡上在编辑器窗口中，在**源计算机的文件**，打开快捷菜单**游戏的主输出**选择**复制**。  
  
13. 下的空白处打开快捷菜单**名称**中的列**目标计算机的文件**，然后选择**粘贴**。 名为的新项**Game.Primary Output**显示。  
  
14. 在**解决方案资源管理器**下**指定应用程序数据**节点，打开**可再发行文件**页。  
  
15. 上**可再发行组件 （游戏安装程序）**在编辑器窗口中，选择的选项卡**Visual c + + 11.0 CRT (x86)**复选框。  
  
16. 在菜单栏上，选择**生成**，**生成解决方案**生成游戏项目和游戏安装程序项目。  
  
17. 在解决方案文件夹中，找到从游戏安装程序项目生成的 setup.exe 程序，然后运行该程序将游戏应用程序安装到计算机上。 可在另一台计算机上复制此文件，来安装应用程序及其所需的库文件。  
  
18. 可以在安装项目中设置多个选项，满足你的需求。 有关详细信息，在**解决方案资源管理器**下**游戏安装程序**项目中，打开**入门**页，然后选择 F1 键打开 ISLE help library。  
  
## <a name="next-steps"></a>后续步骤  
 **上一步：** [演练： 调试项目 （c + +）](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)  
 [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
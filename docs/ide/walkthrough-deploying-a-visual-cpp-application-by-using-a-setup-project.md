---
title: "演练：使用安装项目部署 Visual C++ 应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "针对 Visual C++ 的部署"
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：使用安装项目部署 Visual C++ 应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述如何使用安装项目部署 Visual C\+\+ 应用程序。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   安装有 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 的计算机。  
  
-   另一台没有 Visual C\+\+ 库的计算机。  
  
### 使用安装项目部署应用程序  
  
1.  使用**“MFC 应用程序向导”**创建新的 Visual Studio 解决方案。  若要查找该向导，请从**“新建项目”**对话框中，展开**“Visual C\+\+”**节点，选择**“MFC”**，再选择**“MFC 应用程序”**，输入项目的名称，然后单击**“确定”**。  
  
2.  将活动解决方案配置更改为**“发布”**。  从**“生成”**菜单中，选择**“配置管理器”**。  从**“配置管理器”**对话框的**“活动解决方案配置”**下拉框中选择**“发布”**。  
  
3.  按 F7 以生成该应用程序。  或者，在**“生成”**菜单上，单击**“生成解决方案”**。  这使安装项目使用此 MFC 应用程序项目输出。  
  
4.  如果尚未这样做，请下载 InstallShield limited Edition \(isle\)，在 Visual Studio 开发人员可以自由并替换项模板函数在 Visual Studio 安装和部署的。  如果连接到 Internet 时，请打开 **新建项目** 对话框中选择 **文件**，**新建**，在菜单栏上 **项目**，或者通过右击所在 **解决方案资源管理器** 的解决方案并选择 **添加**，**新建项目…**。  外接 **其他项目类型** 节点，请在 **安装和部署** 节点的 **启用 InstallShield Limited Edition**，并按照显示的命令。  一旦下载，安装并激活的 InstallShield limited Edition，关闭的 Visual Studio 并重新打开它。  
  
5.  再次打开 **新建项目** 对话框中，展开 **其他项目类型** 节点，然后选择在 **InstallShield Limited Edition** 节点的 **InstallShield Limited Edition 项目**。  
  
6.  按照 InstallShield limited Edition 模板创建的安装项目的 **入门** 节点的命令添加输出引用添加到您的 Visual Studio MFC 项目。  
  
7.  生成安装项目以创建安装程序文件 \(setup.exe\)。  为此，请右击该 **解决方案资源管理器** 的安装项目节点并选择 **生成**。  
  
     InstallShield limited Edition 在安装项目节点构树创建一组文件（默认情况下，它可以位于安装项目的 Express\\SingleImage\\DiskImages\\DISK1 子文件夹中）。  
  
8.  运行在没有 Visual C\+\+ 库的另一台计算机上安装程序。  
  
## 请参阅  
 [部署示例](../ide/deployment-examples.md)
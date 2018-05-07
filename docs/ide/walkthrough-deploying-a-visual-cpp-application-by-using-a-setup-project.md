---
title: 通过使用安装项目部署 Visual c + + 应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 454507a3a3f33b43af0e50c25dab6703aa75a56b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>演练：使用安装项目部署 Visual C++ 应用程序
描述如何使用安装项目部署 Visual c + + 应用程序。  
  
## <a name="prerequisites"></a>系统必备  
 你需要以下组件来完成本演练：  
  
-   与计算机[!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)]安装。  
  
-   其他计算机未安装 Visual c + + 库。  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>通过使用安装项目部署应用程序  
  
1.  使用**MFC ApplicationWizard**创建新的 Visual Studio 解决方案。 若要查找该向导，从**新项目**对话框框中，展开**Visual c + +** 节点中，选择**MFC**，选择**MFC 应用程序**，输入为项目命名，再单击**确定**。  
  
2.  更改活动解决方案配置到**版本**。 从**生成**菜单上，选择**Configuration Manger**。 从**Configuration Manager**对话框中，选择**版本**从**活动解决方案配置**下拉框。  
  
3.  按 F7 以生成应用程序。 或在**生成**菜单上，单击**生成解决方案**。 这使安装程序项目以使用此 MFC 应用程序项目的输出。  
  
4.  如果你尚未这样做，下载 InstallShield Limited Edition (ISLE)，这是免费的 Visual Studio 开发人员，并替换为安装和部署 Visual Studio 中的项目模板的功能。 当你连接到 Internet 时，打开**新项目**对话框中，通过选择**文件**，**新建**，**项目**上在菜单栏，或通过右键单击你的解决方案中**解决方案资源管理器**并选择**添加**，**新项目**。 展开**其他项目类型**节点，选择**启用 InstallShield Limited Edition**中**安装和部署**节点，然后按照显示的说明进行操作。 一旦你已下载、 安装并激活 InstallShield Limited Edition，关闭 Visual Studio 并重新打开它。  
  
5.  打开**新项目**对话框中再次，展开**其他项目类型**节点，然后选择**InstallShield Limited Edition 项目**中**InstallShield Limited Edition**节点。  
  
6.  按照说明进行操作中的**入门**InstallShield Limited Edition 模板添加到你的 Visual Studio MFC 项目输出引用创建的安装程序项目节点。  
  
7.  生成安装项目来创建安装程序文件 (setup.exe)。 为此，请右键单击中的安装程序项目节点**解决方案资源管理器**和选择**生成**。  
  
     在安装程序项目树中，InstallShield Limited Edition 创建安装程序文件 （默认情况下，它可能会出现在安装项目的 Express\SingleImage\DiskImages\DISK1 子文件夹）。  
  
8.  在没有 Visual c + + 库的第二个计算机上运行安装程序。  
  
## <a name="see-also"></a>请参阅  
 [部署示例](../ide/deployment-examples.md)
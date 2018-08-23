---
title: 使用安装项目部署 Visual C++ 应用程序 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332775"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>演练：使用安装项目部署 Visual C++ 应用程序
介绍如何使用安装项目部署 Visual C++ 应用程序。  
  
## <a name="prerequisites"></a>系统必备  
 你需要以下组件来完成本演练：  
  
-   已安装 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 的计算机。  
  
-   另一台没有 Visual C++ 库的计算机。  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>使用安装项目部署应用程序  
  
1.  使用 MFC 应用程序向导创建新的 Visual Studio 解决方案。 要查找该向导，请在“新建项目”对话框中展开“Visual C++”节点，依次选择“MFC”、“MFC 应用程序”，输入项目的名称，然后单击“确定”。  
  
2.  将活动解决方案配置更改为“发布”。 从“生成”菜单中，选择“Configuration Manager”。 从“Configuration Manager”对话框的“活动解决方案配置”下拉框中选择“发布”。  
  
3.  按 F7 生成应用程序。 或者，在“生成”菜单上，单击“生成解决方案”。 此操作可使安装项目使用此 MFC 应用程序项目的输出。  
  
4.  如果尚未执行此操作，请下载对 Visual Studio 开发人员免费的 InstallShield Limited Edition (ISLE)，并替换 Visual Studio 中项目模板的功能以进行安装和部署。 连接到 Internet 后，通过在菜单栏上依次选择“文件”、“新建”、“项目”，或右键单击“解决方案资源管理器”中的解决方案，然后依次选择“添加”、“新建项目”来打开“新建项目”对话框。 展开“其他项目类型”节点，在“安装和部署”节点中选择“启用 InstallShield Limited Edition”，然后按照显示的说明进行操作。 下载、安装并激活 InstallShield Limited Edition 后，请关闭 Visual Studio，然后重新打开它。  
  
5.  再次打开“新建项目”对话框，展开“其他项目类型”节点，然后在“InstallShield Limited Edition”节点中选择“InstallShield Limited Edition 项目”。  
  
6.  按照 InstallShield Limited Edition 模板创建的安装项目的“入门”节点中的说明，将输出引用添加到 Visual Studio MFC 项目中。  
  
7.  生成安装项目以创建安装程序文件 (setup.exe)。 要执行此操作，请右键单击“解决方案资源管理器”中的安装项目节点，然后选择“生成”。  
  
     InstallShield Limited Edition 将在安装项目树中创建安装文件（默认情况下，它可能位于安装项目的 Express\SingleImage\DiskImages\DISK1 子文件夹中）。  
  
8.  在没有 Visual C++ 库的第二台计算机上运行安装程序。  
  
## <a name="see-also"></a>请参阅  
 [部署示例](../ide/deployment-examples.md)
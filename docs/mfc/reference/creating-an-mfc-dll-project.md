---
title: "创建 MFC DLL 项目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcdll.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 创建"
  - "DLL [C++], MFC"
  - "MFC DLL [C++], 创建项目"
  - "项目 [C++], 创建"
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 创建 MFC DLL 项目
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC DLL 是作为可由多个应用程序同时使用的共享函数库的二进制文件。  创建 MFC DLL 项目的最容易方法是使用 MFC DLL 向导。  
  
> [!NOTE]
>  IDE 中功能的外观取决于您的当前设置或版本，可能与帮助中的描述不同。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 使用 MFC DLL 向导创建 MFC DLL 项目  
  
1.  按照帮助主题[用 Visual C\+\+ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。  
  
 **注意** 在**“新建项目”**对话框中，选择“模板”窗格中的 `MFC DLL` 图标以打开 MFC DLL 向导。  
  
1.  使用 [MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)的[应用程序设置](../../mfc/reference/application-settings-mfc-dll-wizard.md)页定义应用程序设置。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
2.  单击**“完成”**关闭向导，然后在**“解决方案资源管理器”**中打开新项目。  
  
 创建了项目后，可以在“解决方案资源管理器”中查看创建的文件。  有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。  有关文件类型的更多信息，请参见[为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## 请参阅  
 [Visual C\+\+ 项目类型](../Topic/Debugging%20Preparation:%20Visual%20C++%20Project%20Types.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)
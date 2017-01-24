---
title: "创建 ATL 项目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MIN_CRT 宏"
  - "ATL 项目, 创建"
  - "ATL70.DLL"
  - "用 ATL 组件分发文件"
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建 ATL 项目
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建 ATL 项目时，最简单的方法是使用 ATL 项目向导，该向导位于**“新建项目”对话框**的 Win32 项目文件夹下。  
  
### 使用 ATL 项目向导创建 ATL 项目  
  
1.  按照帮助主题[用 Visual C\+\+ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明操作。  
  
2.  在“模板”窗格中选择**“ATL 项目”**图标以打开 ATL 项目向导。  
  
3.  使用 `ATL Project Wizard`的[“应用程序设置”](../../atl/reference/application-settings-atl-project-wizard.md)页定义应用程序设置。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
4.  单击“完成”关闭向导并在开发环境中打开新项目。  
  
 创建项目后，可在**解决方案资源管理器**中查看创建的文件。  有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。  有关文件类型的更多信息，请参见[为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  有关新 ATL 项目的配置以及更改这些配置的方法的更多信息，请参见[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)。  
  
## 请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)
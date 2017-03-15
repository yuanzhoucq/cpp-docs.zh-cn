---
title: "向空的 Win32 应用程序添加文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "空白项目"
  - "空项目, 添加文件"
  - "文件 [C++], 添加到项目"
  - "项目 [C++], 添加项"
ms.assetid: 070098e8-0396-49fe-a697-3daa2f1be6de
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 向空的 Win32 应用程序添加文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 向空的 Windows 桌面应用程序添加文件  
  
1.  在“解决方案资源管理器”中选择目录。  
  
2.  右键单击目录名称，在快捷菜单中单击“添加”，然后单击“现有项”。  
  
3.  在“添加现有项”对话框中，导航到想要添加到项目中的文件。  
  
4.  单击“确定”。  
  
 要向项目中添加既不是源文件、头文件也不是资源文件的文件，请右键单击解决方案资源管理器中的解决方案节点，然后以相同的方法将文件添加到项目中。 将创建杂项文件夹来保存项目中的其他文件。  
  
> [!NOTE]
>  在生成项目之前，需要指定这些文件的生成选项，以便将文件正确地添加到已完成的应用程序中。 有关详细信息，请参阅[通过属性页指定项目设置](../ide/property-pages-visual-cpp.md)和[生成 C\/C\+\+ 程序](../build/building-c-cpp-programs.md)。  
  
## 请参阅  
 [正在创建空的 Windows 桌面应用程序](../windows/creating-an-empty-windows-desktop-application.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)
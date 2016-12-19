---
title: "添加 MFC 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes.adding.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 添加 MFC"
  - "MFC, 添加类"
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加 MFC 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要将从 Microsoft 基础类 \(MFC\) 库类导出的类添加到项目，请从[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中调用“添加类”命令。  指定新类的名称，选择基类，并选择与它关联的对话框 ID（如果有）。  代码向导创建头文件和实现文件并将它们添加到项目。  
  
> [!NOTE]
>  如果最初[创建了具有 MFC 支持的 ATL COM 应用程序](../../atl/reference/mfc-support-in-atl-projects.md)，可以将 MFC 类添加到该应用程序中。  也可以将 MFC 类添加到具有 MFC 支持的 Win32 项目中。  
  
### 将 MFC 类添加到项目  
  
1.  从“类视图”中，右击项目名称。  单击“添加”，然后单击“添加类”打开[添加类](../../ide/add-class-dialog-box.md)对话框。  
  
2.  在“模板”窗格中，选择**“MFC 类”**，然后按**“添加”**按钮。  
  
3.  在 [MFC 类向导](../../mfc/reference/mfc-add-class-wizard.md)对话框中定义新类的设置。  
  
4.  单击“完成”关闭向导并在类视图中查看新类。  也可以在**解决方案资源管理器**中查看向导创建的文件。  
  
## 请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [类概述](../../mfc/class-library-overview.md)
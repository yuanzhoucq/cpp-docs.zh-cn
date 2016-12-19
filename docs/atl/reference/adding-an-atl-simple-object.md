---
title: "添加 ATL 简单对象 | Microsoft Docs"
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
  - "vc.codewiz.classes.adding.atl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加对象"
  - "ATL, 简单对象"
  - "对象 [ATL]"
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加 ATL 简单对象
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要向项目中添加 ATL（活动模板库）对象，项目必须已创建为 ATL 应用程序或者包含 ATL 支持的 MFC 应用程序。  可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或者[向 MFC 应用程序项目添加 ATL 对象](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
 第一次创建新的 ATL 对象时，可以为它定义 COM 接口，或者以后使用“类视图”快捷菜单中的[实现接口](../../ide/implement-interface-wizard.md)命令添加 COM 接口。  
  
### 向 ATL COM 项目中添加 ATL 简单对象  
  
1.  在**“解决方案资源管理器”**或[类视图](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击要向其添加 ATL 简单对象的项目的名称。  
  
2.  从快捷菜单中单击“添加”，然后单击“添加类”。  
  
3.  在[“添加类”](../../ide/add-class-dialog-box.md)对话框中的“模板”窗格中，单击**“ATL 简单对象”**，然后单击**“打开”**显示 [ATL 简单对象向导](../../atl/reference/atl-simple-object-wizard.md)。  
  
4.  在“ATL 简单对象向导”的[选项](../../atl/reference/options-atl-simple-object-wizard.md)页上为项目设置附加选项。  
  
5.  单击“完成”，将对象添加到项目中。  
  
## 请参阅  
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [在 ATL 项目中添加新接口](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)   
 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md)   
 [添加方法](../../ide/adding-a-method-visual-cpp.md)   
 [MFC 类](../../mfc/reference/adding-an-mfc-class.md)   
 [添加一般 C\+\+ 类](../../ide/adding-a-generic-cpp-class.md)
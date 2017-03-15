---
title: "添加 ATL 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加控件"
  - "控件 [ATL], 添加到项目"
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 添加 ATL 控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此向导向项目中添加支持所有潜在容器接口的用户接口对象。  若要支持这些接口，项目必须已创建为 ATL 应用程序或包含 ATL 支持的 MFC 应用程序。  可使用 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或者[向 MFC 应用程序项目添加 ATL 对象](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
### 向项目中添加 ATL 控件  
  
1.  在**“解决方案资源管理器”**或[类视图](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击要向其添加 ATL 简单对象的项目的名称。  
  
2.  在快捷菜单中单击**“添加”**，然后单击**“添加类”**。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框中的模板窗格中，单击**“ATL 控件”**，然后单击**“添加”**以显示 [ATL 控件向导](../../atl/reference/atl-control-wizard.md)。  
  
 使用**“ATL 控件向导”**，可以创建三种控件之一：  
  
-   标准控件  
  
-   复合控件  
  
-   DHTML 控件  
  
 另外，也可以通过选择向导**“选项”**页面上的**“最小控制”**来缩小控件的大小并删除大多数容器不使用的接口。  
  
## 请参阅  
 [Adding Functionality to the Composite Control](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [ATLFire Sample](http://msdn.microsoft.com/zh-cn/5b2649f1-f45b-4cfb-9c4b-4d9459c26b09)
---
title: "实现接口 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "接口, 实现"
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 实现接口 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为实现接口，必须已创建了作为 ATL COM 应用程序或包含 ATL 支持的 MFC 应用程序的项目。  可使用 [ATL 项目向导](../atl/reference/atl-project-wizard.md)创建 ATL 应用程序，或者[向 MFC 应用程序项目添加 ATL 对象](../mfc/reference/adding-atl-support-to-your-mfc-project.md)以实现 MFC 应用程序的 ATL 支持。  
  
 创建项目后，要实现接口，必须先添加 ATL 对象。  有关向 ATL 项目添加对象的向导列表，请参见[向 ATL 项目添加对象和控件](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
> [!NOTE]
>  该向导不支持 ATL 对话框、使用 ATL 的 XML Web services、性能对象或性能计数器。  
  
 如果[添加 ATL 控件](../atl/reference/adding-an-atl-control.md)，可以指定是否实现该向导的[接口](../atl/reference/interfaces-atl-control-wizard.md)页上列出的和 atlcom.h 中定义的默认接口。  
  
 添加了项目或控件后，可以使用“实现接口向导”实现位于任何可用类型库中的其他接口。  
  
 如果添加新接口，必须手动将它添加到项目的 .idl 文件。  有关更多信息，请参见[在 ATL 项目中添加新接口](../atl/reference/adding-a-new-interface-in-an-atl-project.md)。  
  
### 实现接口  
  
1.  在类视图中，右击 ATL 对象的类名。  
  
2.  从快捷菜单中单击“添加”，然后单击**“实现接口”**显示[“实现接口向导”](../ide/implement-interface-wizard.md)。  
  
3.  从适当的类型库中选择要实现的接口并单击“完成”。  
  
4.  在类视图中，展开对象的“基项和接口”节点查看已经实现的接口，然后展开接口的节点查看它的可用属性、方法和事件。  
  
    > [!NOTE]
    >  也可以使用[对象浏览器](http://msdn.microsoft.com/zh-cn/f89acfc5-1152-413d-9f56-3dc16e3f0470)查看接口成员。  
  
## 请参阅  
 [创建 COM 接口](../ide/creating-a-com-interface-visual-cpp.md)   
 [编辑 COM 接口](../ide/editing-a-com-interface.md)
---
title: "你在使用记录视图中的角色（MFC 数据访问） | Microsoft Docs"
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
  - "MFC, 记录视图"
  - "记录视图, 自定义默认代码"
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 你在使用记录视图中的角色（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表介绍了要处理记录集通常必须执行的操作以及框架的用途。  
  
### 使用记录集：你和框架  
  
|你|框架|  
|-------|--------|  
|使用 Visual C\+\+ 对话框编辑器设计窗体。|使用控件创建对话框模板资源。|  
|使用 [MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)创建从 [CRecordView](../mfc/reference/crecordview-class.md) 和 [CRecordset](../mfc/reference/crecordset-class.md) 或从 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 和 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md) 派生的类。|编写你的类。|  
|将记录视图控件映射到记录集字段数据成员。|提供控件和记录集字段之间的 DDX。|  
||提供菜单或工具栏按钮**移动第一个**、**移动最后一个**、**移动下一个**和**移动上一个**命令的默认命令处理程序。|  
||更新对数据源的更改。|  
|\[可选\]编写代码以填充列表框或组合框或包含另一记录集数据的其他控件。||  
|\[可选\]编写用于任何特殊验证的代码。||  
|\[可选\]编写代码以添加或删除记录。||  
  
 基于窗体的编程只是处理数据库的一种方法。  有关使用其他用户界面的应用程序的信息，请参阅 [MFC：使用包含文档和视图的数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)以及 [MFC：使用不含文档和视图的类](../data/mfc-using-database-classes-without-documents-and-views.md)。  有关显示数据库记录的其他方法，请参阅类 [CListView](../mfc/reference/clistview-class.md) 和 [CTreeView](../mfc/reference/ctreeview-class.md)。  
  
## 请参阅  
 [记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)
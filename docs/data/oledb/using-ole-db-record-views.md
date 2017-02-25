---
title: "使用 OLE DB 记录视图 | Microsoft Docs"
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
  - "COleDBRecordView 类, 概述"
  - "MFC, 记录视图"
  - "OLE DB 记录视图"
  - "OLE DB, 记录视图"
  - "记录视图, 记录视图对象"
  - "行集合, 记录视图"
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 OLE DB 记录视图
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果要在 MFC 应用程序中显示 OLE DB 行集合数据，则应使用 MFC 类 [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。  从 `COleDBRecordView` 中创建的记录视图对象使您可以在 MFC 控件中显示数据库记录。  记录视图是一个对话框窗体视图，该视图直接与从 `CRowset` 模板类创建的 OLE DB 行集合对象相连接。  获取此行集合对象的句柄很简单：  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 此视图在对话框的控件中显示 `CRowset` 对象的字段。  `COleDBRecordView` 对象使用对话框数据交换 \(DDX\) 和 `CRowset` 内置的导航功能（**MoveFirst**、`MoveNext`、`MovePrev` 和 `MoveLast`）来自动实现窗体上的控件和行集合的字段之间的数据移动。  `COleDBRecordView` 跟踪行集合中用户的位置以便于记录视图能够更新用户界面并提供 [OnMove](../Topic/COleDBRecordView::OnMove.md) 方法用于在移至另一记录前更新当前记录。  
  
 可以将 DDX 功能与 **COleDbRecordView** 一起使用，以便直接从数据库记录集中获取数据，并在对话框控件中显示它。  应将 **DDX\_\*** 方法（如 `DDX_Text`）而不是 **DDX\_Field\*** 函数（如 `DDX_FieldText`）与 **COleDbRecordView** 一起使用。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)   
 [COleDBRecordView Class](../../mfc/reference/coledbrecordview-class.md)
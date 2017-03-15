---
title: "记录视图类的功能（MFC 数据访问） | Microsoft Docs"
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
  - "记录视图类"
  - "记录视图, 类"
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 记录视图类的功能（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以使用类 [CFormView](../mfc/reference/cformview-class.md) 执行基于窗体的数据访问编程，而通常从 [CRecordView](../mfc/reference/crecordview-class.md) 和 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 类派生更好。  除其 `CFormView` 功能外，还可以使用 `CRecordView` 和 `CDaoRecordView`：  
  
-   提供窗体控件和关联的记录集对象之间的对话框数据交换 \(DDX\)。  
  
-   处理“移动第一个”、“移动下一个”、“移动上一个”和“移动最后一个”命令浏览关联记录集对象中的记录。  
  
-   当用户移动到另一条记录时更新对当前记录的更改。  
  
 有关导航的详细信息，请参阅[记录视图：支持记录视图中的导航](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。  
  
## 请参阅  
 [记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)
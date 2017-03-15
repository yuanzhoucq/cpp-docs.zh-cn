---
title: "清理文档和视图 | Microsoft Docs"
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
  - "文档, 清理"
  - "文档, 关闭"
  - "视图, 清理"
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 清理文档和视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在文档关闭时，框架首次调用 [DeleteContents](../Topic/CDocument::DeleteContents.md) 成员函数。  如果指导性文档操作期间分配堆上的任何内存，`DeleteContents` 是其释放的最佳位置。  
  
> [!NOTE]
>  不应该释放在文档的析构函数的文档数据。  在 SDI 应用程序，可能重用文档对象。  
  
 可以重写视图的析构函数释放在堆分配的任何内存。  
  
## 请参阅  
 [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)
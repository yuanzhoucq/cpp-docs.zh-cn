---
title: "从 CDocument 派生文档类 | Microsoft Docs"
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
  - "CDocument 类, 派生自"
  - "类 [C++], 派生自 CDocument"
  - "派生类, 经常重写的函数"
  - "文档类, 经常重写的函数"
  - "文档对象, 派生"
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 从 CDocument 派生文档类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档包含和管理应用程序数据。  若要将 MFC 应用程序提供向导提供的文档。类，则必须执行以下操作：  
  
-   从文档的每种类型的 **CDocument** 派生一个类。  
  
-   添加成员变量存储每个文档中的数据。  
  
-   **CDocument** `Serialize` 文档中重写类的成员函数。  `Serialize` 进出磁盘写入并读取文档的数据。  
  
## 其他文档通常重写的函数  
 可能还要重写其他 **CDocument** 成员函数。  具体而言，您通常需要重写和 [OnNewDocument](../Topic/CDocument::OnNewDocument.md)[OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 初始化文档的数据成员和 [DeleteContents](../Topic/CDocument::DeleteContents.md) 销毁动态分配的数据。  有关可重写成员的信息，请参见 [CDocument](../mfc/reference/cdocument-class.md) " *MFC 参考"中的*类。  
  
## 请参阅  
 [使用文档](../mfc/using-documents.md)
---
title: "初始化文档和视图 | Microsoft Docs"
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
  - "文档, 初始化"
  - "初始化文档"
  - "初始化对象, 文档对象"
  - "初始化视图"
  - "视图, 初始化"
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 初始化文档和视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档以两种不同的方式创建，因此，类文档必须支持这两种方式。  首先，用户可以使用文件新建命令创建一个新的空白文档。  在这种情况下，请在 [CDocument](../mfc/reference/cdocument-class.md)[OnNewDocument](../Topic/CDocument::OnNewDocument.md) 初始化类的成员函数的重写的文档。  其次，用户可以使用文件菜单上的打开命令来创建一个新的文档，其内容从一个文件中读取。  在这种情况下，初始化文件在你的**CDocument**类的[OnNewDocument](../Topic/CDocument::OnOpenDocument.md)成员函数的重写。  如果两个初始化操作相同，可以从两个重写的常用成员函数，或 `OnOpenDocument` 可以调用 `OnNewDocument` 初始化干净的文档然后完成打开操作。  
  
 创建自己的文件后创建的视图。  初始化一个视图的最佳时间是后框架已完成创建文档，框架窗口和视图。  你可以通过重写[CView](../mfc/reference/cview-class.md)的[OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)成员函数初始化你的视图。  如果你需要每次都重新初始化或调整任何该文件的变化，你可以重写[OnUpdate](../Topic/CView::OnUpdate.md)。  
  
## 请参阅  
 [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)
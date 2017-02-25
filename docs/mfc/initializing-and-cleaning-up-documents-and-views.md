---
title: "初始化和清理文档和视图 | Microsoft Docs"
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
  - "文档对象, 生命周期"
  - "文档, 清理"
  - "文档, 初始化"
  - "初始化文档"
  - "初始化对象, 文档对象"
  - "初始化视图"
  - "视图, 清理"
  - "视图, 初始化"
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 初始化和清理文档和视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于初始化和清理使用以下原则在文档和视图后：  
  
-   MFC 框架初始化文档和视图；在您初始化添加到了它们的任何数据。  
  
-   框架清理文档和视图关闭；您必须释放在堆分配。那些文档和视图的成员函数中的所有内存。  
  
> [!NOTE]
>  恢复整个应用程序中初始化在类 `CWinApp`中的 [InitInstance](../Topic/CWinApp::InitInstance.md) 成员函数的重写完成，因此，整个应用程序清理最适合在 `CWinApp` 成员函数的重写完成 [ExitInstance](../Topic/CWinApp::ExitInstance.md)。  
  
 一个文档的生命周期及其视图和视图\) 或框架窗口 \(在 MDI 应用程序如下：  
  
1.  在动态创建时，文档构造函数调用。  
  
2.  对于每个新文档，文档中或 [OnNewDocument](../Topic/CDocument::OnNewDocument.md) [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 调用。  
  
3.  用户与文档交互在其生存期内。  通常，当用户在文档数据，通过视图选择和编辑数据，此错误发生。  视图更改为传递存储和更新视图的其他文档。  在此期间文档和视图可能处理命令。  
  
4.  框架调用 [DeleteContents](../Topic/CDocument::DeleteContents.md) 删除数据到特定文档。  
  
5.  文档的析构函数调用。  
  
 在 SDI 应用程序，那么，当文档首先创建时，第 1 步执行一次。  然后，在步骤 2 到 4 打开，重复执行新文档。  新文档重复使用现有的文档对象。  最后，那么，当应用程序关闭时，像步骤 5。  
  
## 您想进一步了解什么？  
  
-   [初始化文档和视图](../mfc/initializing-documents-and-views.md)  
  
-   [清理文档和视图](../mfc/cleaning-up-documents-and-views.md)  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)
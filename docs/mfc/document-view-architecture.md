---
title: "文档/视图体系结构 | Microsoft Docs"
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
  - "CDocument 类"
  - "CView 类, 视图体系结构"
  - "文档对象"
  - "文档对象, 文档/视图体系结构"
  - "文档对象, MFC 文档/视图模型"
  - "文档, MFC 文档/视图模型"
  - "MFC, 文档"
  - "MFC, 视图"
  - "视图, MFC 文档/视图模型"
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 文档/视图体系结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，" MFC 应用程序向导"创建。类文档和视图类的应用程序"  管理 MFC 数据分割到这两个类。  文档存储您的数据并管理更新打印数据的多个视图的数据的、和坐标。  视图显示数据并管理用户与它交互的，包括选择和编辑。  
  
 在此模型，所以 MFC 文档对象读写数据到永久存储。  文档还提供接口。数据，无论该类型所驻留 \(如数据库\)。  单独视图对象控制数据显示，从所呈现窗口中的数据向用户选择和编辑数据。  视图从文档中显示数据并传达回所有文档数据更改。  
  
 当您可以很容易重写或忽略文档\/视图分开，则强制原因很多情况下此模型。  一种更好。需要相同文档的多个视图，如电子表格和图表视图。  文档\/视图模型允许单独视图对象表示的每个数据视图，而代码，共有的所有显示 \(如计算引擎可以驻留文档。  本文档还利用更新的所有任务，每当数据发生更改。  
  
 MFC 文档\/视图体系结构可以轻松支持多视图、多文档类型、拆分窗口和其他重要的用户界面功能。  
  
 MFC 框架的部分最明显至用户并为您，程序员，是文档和视图。  在大部分开发应用程序中使用框架访问编写文档和视图类。  本文描述系列：  
  
-   文档和视图的目的，并且它们在框架进行交互。  
  
-   您必须实现自己执行。  
  
 核心文档\/视图中心是四个关键类：  
  
 [CDocument](../mfc/reference/cdocument-class.md) \( [COleDocument](../mfc/reference/coledocument-class.md)\) 或类支持使用的对象存储或控制程序的数据和用于根据程序员定义的文档类的基本功能。  文档表示用户通常会打开与在"文件"菜单中打开命令并保存。在"文件"菜单上的"保存"命令数据的单元。  
  
 [CView](../mfc/reference/cview-class.md) \(或派生类之一\) 对程序员定义的视图类的基本功能。  视图与文档并充当了文档和用户之间的中间组件：视图呈现文档的图像在屏幕上并解释用作操作用户输入处理文档。  视图还呈现打印和"打印预览"的图像。  
  
 其差异[CFrameWnd](../mfc/reference/cframewnd-class.md) \(一个\) 支持在文档的一个或多个视图四周的框架的对象。  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) \(或或 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)\) 支持对象坐标特定类型的一个或多个现有文档和管理创建正确的文档、视图和框架窗口对象该类型。  
  
 下图显示了记录视图的文档和它的视图之间的关系。  
  
 ![视图是所显示文档的一部分](../mfc/media/vc379n1.png "vc379N1")  
文档和视图  
  
 文档\/视图实现类库中将数据从其显示以及对数据的用户操作。  对数据所做的任何更改都将在文档中的类管理。  视图调用此接口来访问和以更新数据。  
  
 文档、它们的关联视图和构成视图的框架窗口由文档模板创建。  文档模板负责创建和管理的文档类型中所有文档负责。  
  
## 您想进一步了解什么？  
  
-   [文档\/视图结构的纵览](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [文档\/视图结构的优点](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [应用程序向导创建的文档和视图类](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [文档\/视图结构的替换选项](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [向单个文档添加多个视图](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [使用文档](../mfc/using-documents.md)  
  
-   [使用视图](../mfc/using-views.md)  
  
-   [多个文档类型、视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [初始化自己添加文档 & 视图类](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [不结合文档和视图使用数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [示例](../top/visual-cpp-samples.md)  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [窗口](../mfc/windows.md)   
 [框架窗口](../mfc/frame-windows.md)   
 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档\/视图创建](../mfc/document-view-creation.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)
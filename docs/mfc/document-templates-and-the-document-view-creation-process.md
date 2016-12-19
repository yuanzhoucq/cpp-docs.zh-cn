---
title: "文档模板和文档/视图创建过程 | Microsoft Docs"
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
  - "CDocTemplate 类"
  - "文档模板, 和视图"
  - "文档/视图体系结构, 创建文档/视图"
  - "图标, 对于多个文档模板"
  - "MFC, 文档模板"
  - "多个文档模板"
  - "单个文档模板"
  - "模板, 文档模板"
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文档模板和文档/视图创建过程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要管理创建及其相关视图的复杂进程和文档框架窗口，框架使用两个文档模板类： 在SDI应用程序中[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)和[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) 对 MDI 应用程序。  `CSingleDocTemplate` 可以同时创建和存储一个类型的文档。  `CMultiDocTemplate` 保留多个同一类型的打开文档的列表。  
  
 某些应用程序可以支持多文档类型。  例如，应用程序可能支持文本文档和图件。  在这种应用程序中，当用户选择文件菜单上的新命令时，一个对话框会显示可能的要打开的新文件的列表。  对于每个支持的文档类型，应用程序使用不同的文档模板对象。  下图说明了支持两种文档类型和显示多个打开文档的MDI 应用程序的配置。  
  
 ![具有两种文档类型的 MDI 应用程序](../mfc/media/vc387h1.png "vc387H1")  
包含两个文档类型的 MDI 应用程序  
  
 文档模板将应用程序对象创建和维护。  在应用程序的 `InitInstance` 函数执行时的一个关键任务是构造一个或多个正确的文档模板类型。  此功能在[创建文档模板](../mfc/document-template-creation.md)中描述。  应用程序对象在其模板列表中，存储了一个指向每个文件模板的指针并且为增加文件模板提供一个接口。  
  
 如果需要支持两个或多个文档类型，则必须为每个文档类型添加一额外的调用[AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)。  
  
 根据其在应用程序文档模板列表中的位置，为每个文档模板注册一个图标。  文档模板的顺序是由调用`AddDocTemplate`来添加他们的顺序所决定的。  MFC 假定，应用程序的第一个图标资源是应用程序图标，下一个图标资源是第一文档图标，依此类推。  
  
 例如，文档模板是应用程序中的第三个。  如果在应用程序的图标资源位于索引 3 处，则该图标是用于文档模板。  否则，图标索引值为 0 ，则作为默认图标。  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [文档模板创建](../mfc/document-template-creation.md)   
 [文档\/视图创建](../mfc/document-view-creation.md)   
 [MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)
---
title: "MFC 应用程序向导创建的文档和视图类 | Microsoft Docs"
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
  - "应用程序向导 [C++], 创建的文档/视图类"
  - "文档类"
  - "文档类, 由应用程序向导创建"
  - "视图类, 由应用程序向导创建"
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 应用程序向导创建的文档和视图类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 应用程序向导将创建您的骨骼文档和视图类提供了在开发程序的提供了一个良好的开端。  可以 [命令、消息映射到这些类](../mfc/reference/mapping-messages-to-functions.md) 和使用 Visual C\+\+ 源代码编辑器编写它们的成员函数。  
  
 MFC 应用程序向导"创建的文档从类派生。[CDocument](../mfc/reference/cdocument-class.md) 视图类从派生。[CView](../mfc/reference/cview-class.md) 名称应用程序向导产生包含这些类和文件基于您在向导"提供的应用程序项目名称。  在应用程序向导，可以使用生成的类的页修改默认名称。  
  
 一些应用程序可能需要多个类文档、视图类或框架窗口类。  有关更多信息，请参见 [多文档类型、视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)
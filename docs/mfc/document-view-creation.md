---
title: "文档/视图创建 | Microsoft Docs"
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
  - "文档/视图体系结构, 创建文档/视图"
  - "文档, 创建"
  - "MFC, 文档"
  - "MFC, 视图"
  - "对象创建器"
  - "表 [C++]"
  - "表 [C++], 每个 MFC 对象创建的对象"
  - "视图, 和框架窗口"
  - "视图, 创建"
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文档/视图创建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架提供 `New` 和 **打开** 命令的实现 \(以下内容 \(当然\) 在 **文件** 菜单。  新文档及其关联视图和框架窗口中是创建在应用程序对象、文档模板生成文档、新的和新生成的框架窗口中的团队成果。  下表汇总了的对象创建。  
  
### Creator 对象  
  
|Creator|创建|  
|-------------|--------|  
|Application 对象|文档模板|  
|文档模板|Document|  
|文档模板|框架窗口|  
|框架窗口|视图|  
  
## 请参阅  
 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档模板创建](../mfc/document-template-creation.md)   
 [MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)
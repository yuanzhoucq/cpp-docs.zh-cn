---
title: "文档模板创建 | Microsoft Docs"
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
  - "构造函数 [C++], 文档模板"
  - "文档模板"
  - "文档模板, 创建"
  - "MFC, 文档模板"
  - "模板, 文档模板"
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 文档模板创建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当创建新文档根据从 **文件** 菜单中的一个 `New` 或 **打开** 命令，文档模板来查看创建文档的框架窗口。  
  
 文档模板构造函数指定类型的文档、窗口和视图模板可以创建。  传递给构造函数的参数。这依赖文档模板  下面的代码演示示例应用程序 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) 中创建的：  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/CPP/document-template-creation_1.cpp)]  
  
 为新的 `CMultiDocTemplate` 对象的指针使用为 [AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)的参数。  为由 `CMultiDocTemplate` 构造函数的参数资源 ID 与文档类型的菜单和快捷键并使用 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) 三宏的使用。  返回`RUNTIME_CLASS` 作为其参数命名的 C\+\+ 类的对象。[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 三个 `CRuntimeClass` 对象传递到信息需要在文档创建过程中创建指定的类的新对象的文档模板构造函数提供。  示例显示创建具有附加的 `CScribView` 对象的 `CScribDoc` 文档模板对象的创建。  视图由标准 MDI 子框架窗口构成。  
  
## 请参阅  
 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档\/视图创建](../mfc/document-view-creation.md)   
 [MFC 对象之间的关系](../mfc/relationships-among-mfc-objects.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)
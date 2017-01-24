---
title: "文档模板类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.document"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文档模板, 类"
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文档模板类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当新的文档或视图创建时，文档模板对象协调文件为显示框架窗口对象。  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
 文档模板的基类。  可以直接将不使用该类；相反，您使用从该类派生的其他文档模板类之一。  
  
 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)  
 文档的模板在多文档界面 \(MDI\) 。  MDI 应用程序可以同时打开了多个文档。  
  
 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)  
 文档的模板处于单文档界面 \(SDI\) 。  SDI 应用程序一次只能处于打开的文档。  
  
## 相关的类  
 [CCreateContext](../mfc/reference/ccreatecontext-structure.md)  
 结构传递文档模板的窗口协调文件、创建函数提供视图和框架窗口对象。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
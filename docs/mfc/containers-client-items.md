---
title: "容器：客户端项 | Microsoft Docs"
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
  - "客户端项和 OLE 容器"
  - "OLE 容器, 客户端项"
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 容器：客户端项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文解释客户项是什么并且应用程序从哪些类派生其客户项。  
  
 客户项是包含或引用 OLE 容器应用程序的文档的属于另一应用程序的数据项。  客户项包含潜入在文档中的数据，数据存储在通过连接的容器文档引用的其他位置。  
  
 在 OLE 应用程序的文档类从类 **CDocument** 派生而不是从 [COleDocument](../mfc/reference/coledocument-class.md) `COleDocument` 类为基于 MFC 应用程序中使用文档\/视图结构从 **CDocument** 继承所需的所有功能。  `COleDocument` 还定义将文档作为 `CDocItem` 对象的集合的接口。  为添加，检索和删除该集合的元素提供一些 `COleDocument` 成员函数。  
  
 每个容器应用程序应从 `COleClientItem` 派生至少一个类。  此类对象在 OLE 文档表示项，嵌入或链接。  除非从文档删除这些对象，不然这些对象出现在包含其文档的整个生存期中。  
  
 `CDocItem` 是 `COleClientItem` 和 `COleServerItem` 的基类。  类的对象从这两各自派生，作为在 OLE 项4和客户\/服务器应用程序之间的中介。  每当新的 OLE 项添加到文档，MFC 框架添加客户端应用程序的 `COleClientItem` 的新对象 \- 对 `CDocItem` 对象的文档的集合的派生类。  
  
## 请参阅  
 [容器](../mfc/containers.md)   
 [容器：复合文件](../mfc/containers-compound-files.md)   
 [容器：用户界面问题](../mfc/containers-user-interface-issues.md)   
 [容器：高级功能](../mfc/containers-advanced-features.md)   
 [COleClientItem Class](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem Class](../mfc/reference/coleserveritem-class.md)
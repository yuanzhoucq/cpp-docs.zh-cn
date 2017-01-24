---
title: "文档类 | Microsoft Docs"
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
  - "文档类"
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文档类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档对象类，由文档模板对象创建，来管理应用程序数据。  您将从这些类之一为您的文档派生类。  
  
 文档类对象与视图对象交互。  视图对象表示窗口的工作区，显示文档的数据，并允许用户与之交互。  文档和视图由文档模板对象创建。  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 应用程序特定文档的基类。  从 **CDocument**派生一个或多个文档类。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 用于复合文档的实现，与基本容器中支持的一样。  作为从 [CDocItem](../mfc/reference/cdocitem-class.md) 派生的类的容器使用，  此类可用作容器文档的基类并且是 `COleServerDoc` 的基类。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 从 `COleDocument` 中派生的类提供链接的基础结构。  如果希望它们支持到嵌入对象的连接，您应从此类派生应用程序的文档容器类 ，而不是从 `COleDocument` 。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 保持 OLE 项的客户项列表在富编辑控件中。  使用 [CRichEditView](../mfc/reference/cricheditview-class.md) 和 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 用作基类、服务器应用程序类的文档。  `COleServerDoc` 对象通过与 [COleServerItem](../mfc/reference/coleserveritem-class.md) 对象交互提供大多数服务器支持。  使用类库的文档\/视图结构，编辑功能的可视化对象提供。  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 规定，利用 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)， Web 浏览器 HTML 编辑平台的功能在 MFC 文档视图体系结构上下文中提供 。  
  
## 相关类  
 记录类对象可以是持久性的 \(也就是说，它们可以在存储介质写入其状态和读取它）。  MFC 提供 `CArchive` 类帮助实现文档数据到存储介质的转移。  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 与 [CFile](../mfc/reference/cfile-class.md) 对象协作通过序列化实现对象的持久性存储 \(请参见 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。  
  
 文档还可包含 OLE 对象。  `CDocItem` 是服务器和客户端项的基类。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 “COleClientItem” [](../mfc/reference/coleclientitem-class.md "COleClientItem Class") 和 [COleServerItem](../mfc/reference/coleserveritem-class.md) 的抽象基类。  从 `CDocItem` 派生的类对象表示文档的一部分。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
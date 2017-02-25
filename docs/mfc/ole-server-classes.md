---
title: "OLE 服务器类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 组件, 类"
  - "组件类"
  - "OLE 服务器应用程序, 服务器类"
  - "OLE 服务器文档"
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 服务器类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

服务器应用使用这些类。  服务器文档从 `COleServerDoc` 派生而不是从 **CDocument**。  请注意，由于 `COleServerDoc` 派生自 `COleLinkingDoc`，所以服务器文档也可支持链接的容器。  
  
 `COleServerItem` 类表示在其他文档中嵌入或链接的文档或部分。  
  
 `COleIPFrameWnd` 和 `COleResizeBar` 支持就地编辑对象时，在容器时，并且 `COleTemplateServer` 支持文件为\/视图匹配，因此从其他应用程序的 OLE 对象进行编辑。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 用作基类、服务器应用程序类的文档。  `COleServerDoc` 对象通过交互提供大多数服务器支持为 `COleServerItem` 对象。  使用类库的文档\/视图结构，编辑功能的可视化对象提供。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 `COleClientItem` 和 `COleServerItem`的抽象基类。  从 `CDocItem` 派生的类对象表示文档的一部分。  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 用于 OLE 接口表示到 `COleServerDoc` 项。  通常具有 `COleServerDoc` 对象，故表示文档中的嵌入式片段。  在对文档的各个部分支持连接，如果可以在多个 `COleServerItem` 对象，每个都代表一个指向文档的服务器。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 当服务器文档采用后，编辑为视图提供框架窗口。  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 为就地调整提供标准的用户界面。  此类对象与 `COleIPFrameWnd` 对象共同始终使用。  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 使用框架的文档\/视图结构，用于创建文档。  `COleTemplateServer` 对象最为关联 `CDocTemplate`委托对象的工作。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 异常由 OLE 处理的故障。  容器和服务器使用该类。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
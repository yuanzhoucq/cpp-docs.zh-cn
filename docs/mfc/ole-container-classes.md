---
title: "OLE 容器类 | Microsoft Docs"
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
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 类 [C++]"
  - "容器类 [C++]"
  - "容器 [C++], OLE 容器应用程序"
  - "OLE [C++], 类"
  - "OLE 类 [C++]"
  - "可视化编辑 [C++], 类"
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 容器类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

服务器应用使用这些类。  `COleLinkingDoc` 和 `COleDocument` 管理的 `COleClientItem` 对象的集合。  而不是文档从 **CDocument**派生类中，从 `COleLinkingDoc` 或 `COleDocument`派生，则根据是否希望链接的支持到嵌入在文档中的对象。  
  
 使用 `COleClientItem` 对象表示在从其他文档中嵌入或是指向其他文档的文档各 OLE 项。  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 实现活动文档包容。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 用于复合文档的实现，与基本容器中支持的一样。  作为从 `CDocItemCDocItem` 派生的类的容器使用，  此类可用作容器文档的基类并且是 `COleServerDoc` 的基类。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 从 `COleDocument` 中派生的类提供链接的基础结构。  如果希望它们支持到嵌入对象的连接，您应从此类派生应用程序的文档容器类 ，而不是从 `COleDocument` 。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 保持 OLE 项的客户项列表在富编辑控件中。  使用 [CRichEditView](../mfc/reference/cricheditview-class.md) 和 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 `COleClientItem` 和 `COleServerItem`的抽象基类。  从 `CDocItem` 派生的类对象表示文档的一部分。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 表示连接的客户端为一的链接的或嵌入的 OLE 项的客户项类。  从此类派生的项。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供到 Rich Edit 控件存储的一个 OLE 项的客户端访问权限，则使用具有 `CRichEditView` 和 `CRichEditDoc`。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 异常由 OLE 处理的故障。  容器和服务器使用该类。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
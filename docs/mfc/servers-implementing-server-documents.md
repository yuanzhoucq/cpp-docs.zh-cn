---
title: "服务器：实现服务器文档 | Microsoft Docs"
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
  - "OLE 服务器应用程序, 实现 OLE 服务器"
  - "OLE 服务器应用程序, 管理服务器文档"
  - "服务器文档, 实现"
  - "服务器, 服务器文档"
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 服务器：实现服务器文档
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明必须采取成功实现文档服务器的步骤，则在应用程序向导不指定 OLE 服务器选项。  
  
#### 定义服务器记录类  
  
1.  从 `COleServerDoc` 派生类文档而不是 **CDocument**。  
  
2.  创建从 `COleServerItem`派生的服务器项类。  
  
3.  实现服务器文档。类的 `OnGetEmbeddedItem` 成员函数。  
  
     当容器应用程序的用户创建或编辑一个嵌入项时，将调用`OnGetEmbeddedItem`。  应该返回表示整个文档的项。  这应该是 `COleServerItem`的派生的类的对象。  
  
4.  重写 `Serialize` 成员函数将文档序列化的内容。  除非使用它们所表示，在文档的本机数据不需要序列化服务器项列表。  有关更多信息，请参见 *实现服务器项目* 在 [服务器：服务器项目](../mfc/servers-server-items.md) 文章。  
  
 当服务器创建文档时，框架会自动注册与 OLE 系统 DLL 的文档。  此 DLL 允许标识服务器文档。  
  
 有关更多信息，请参见 [COleServerItem](../mfc/reference/coleserveritem-class.md)[COleServerDoc](../mfc/reference/coleserverdoc-class.md) 和在 *类库引用*。  
  
## 请参阅  
 [服务器](../mfc/servers.md)   
 [服务器：服务器项](../mfc/servers-server-items.md)   
 [服务器：实现服务器](../mfc/servers-implementing-a-server.md)   
 [服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)
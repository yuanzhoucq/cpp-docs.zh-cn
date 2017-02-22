---
title: "OLE 相关类 | Microsoft Docs"
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
  - "ActiveX 类 [C++]"
  - "OLE [C++], 类"
  - "OLE 类 [C++]"
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 相关类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类提供了大量不同的服务，从异常到文件输入和输出。  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 当其他容器发来请求，其用于创建项。  此类为工厂的更具体的类型用作基类，包括 `COleTemplateServer`。  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 用于管理与 OLE 轻量远程过程调用 \(LRPC\) 的并发。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 接口提供对复合文件 `CFile` 的访问。  此类 \(从 `CFile` 派生\) 使 MFC 序列化使用 OLE 结构化存储。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 用于允许本地项的移动，重设大小和重新定位。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
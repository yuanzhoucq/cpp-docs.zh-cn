---
title: "容器： 客户端项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa80911ff14d329dc483cd6497393c6c5595ef2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="containers-client-items"></a>容器：客户端项
本文介绍什么是客户端项目以及您的应用程序应从哪些类派生其客户端项目。  
  
 客户端项目是属于包含在 OLE 容器应用程序的文档中或由此类文档引用的其他应用程序的数据项目。 将嵌入其数据包含在文档中的客户端项目；将链接其数据存储在容器文档引用的其他位置的客户端项目。  
  
 OLE 应用程序中的文档类派生自类[COleDocument](../mfc/reference/coledocument-class.md)而不是从**CDocument**。 `COleDocument`类继承自**CDocument**所必需的使用的 MFC 应用程序所基于的文档/视图体系结构的所有功能。 `COleDocument` 还定义将文档视为 `CDocItem` 对象集合的接口。 为了添加、检索和删除该集合的元素，提供了若干 `COleDocument` 成员函数。  
  
 每个容器应用程序应从 `COleClientItem` 派生至少一个类。 此类的对象表示 OLE 文档中的嵌入项目或链接项目。 这些对象在包含其的文档生存期存在，除非从文档中删除它们。  
  
 `CDocItem`是的基类`COleClientItem`和`COleServerItem`。 派生自这两者的类的对象分别充当 OLE 项目与客户端应用程序以及与服务器应用程序之间的中介。 每当将新的 OLE 项目添加到文档时，MFC 框架就会将客户端应用程序 `COleClientItem` 派生类的新对象添加到 `CDocItem` 对象的文档集合。  
  
## <a name="see-also"></a>请参阅  
 [容器](../mfc/containers.md)   
 [容器： 复合文件](../mfc/containers-compound-files.md)   
 [容器： 用户界面问题](../mfc/containers-user-interface-issues.md)   
 [容器： 高级的功能](../mfc/containers-advanced-features.md)   
 [COleClientItem 类](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem 类](../mfc/reference/coleserveritem-class.md)

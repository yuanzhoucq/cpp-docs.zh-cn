---
title: "使用文档数据变量管理数据 | Microsoft Docs"
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
  - "类 [C++], 友元"
  - "集合类 [C++], 由文档对象使用"
  - "数据 [MFC]"
  - "数据 [MFC], 文档"
  - "文档数据 [C++]"
  - "文档 [C++], 数据存储"
  - "友元类"
  - "成员变量 [C++], 文档类"
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用文档数据变量管理数据
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实现文档的数据，文档成员变量的类。  例如，一组程序声明 `CObList` 类型 \- 存储指向 `CObject` 对象的链接列表数据成员。  此列表存储构成徒手画的线描的某点。  
  
 您如何实现文档的成员数据取决于应用程序的特性。  帮助，则“集合的一组类”的 \-，MFC 提供数组列表，并映射字典 \(\)，其中包括基于 C\+\+ 模板的集合 \- 与类一起封装各种常见数据类型 \(如 `CString`、`CRect`、`CPoint`、`CSize`和 `CTime`。  有关这些类的更多信息，请参见" *MFC 参考"中的*[概述类库](../mfc/class-library-overview.md)。  
  
 当定义文档的成员数据，您通常将成员函数添加到类文档设置和获取数据项并对它们执行这些其他有用的操作。  
  
 视图访问文档对象通过使用视图的指针到文档，安装在视图在创建时间。  您可以通过调用 `CView` 成员函数检索在此视图的成员函数的指针 **GetDocument**。  确保将此指针到自己文档类型。  然后可以通过指针访问政府文件的成员。  
  
 如果频繁的数据传输需要直接访问，或者您使用文档的非公共成员的意愿类，您可能希望视图类的友 \(术语在 C\+\+ 文档\) 类。  
  
## 请参阅  
 [使用文档](../mfc/using-documents.md)
---
title: "数组、列表和映射类 | Microsoft Docs"
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
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 类"
  - "集合类, 列表"
  - "集合类, 映射"
  - "列表类"
  - "映射类"
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数组、列表和映射类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于处理数据聚合，类库提供集合类、数组 \(可保存各种对象和预定义类型的列表和映射一组\)。  动态集合大小。  这些类可在所有程序，则编写为 Windows。  但是，它们为实现定义应用程序的文档框架类的数据结构是最有用的。  可以轻松地从这些派生专用的集合类，还可以创建自己的模板类。  有关这些方法的更多信息，请参见知识库文章 [集合](../mfc/collections.md)。  有关集合类模板的列表，请参见 [数组、列表以及映射的模板类](../mfc/template-classes-for-arrays-lists-and-maps.md)文章。  
  
 数组是连续存储在内存的一维数据结构。  它们支持非常快 RAM，因为任何给定元素内存地址可以通过将元素的索引是元素的大小并将结果计算为数组的基址。  但是，数组将非常大，则必须插入元素为数组，因为，超出插入元素的整个数组必须移动留出空间要插入的元素。  数组可根据需要增长和收缩。  
  
 数组类似于列表，但截然不同地存储。  列表中的每个元素也包括一个指向上一条和下一元素，使其一双向链接列表。  因为这样做只涉及更改指针的数组，它很大程度上快添加或删除项。  但是，在任何搜索开始一致，因为需要列表的末尾，搜索列表的开销可能会很大的。  
  
 映射关联一个键值对数据值。  例如，映射的键可以为字符串和数据指针到列表。  将请求映射该指针与特定字符串。  映射为键，因为外观，使用哈希表查找映射快。  添加和移除项来快。  映射通常与其他数据结构作为访问索引。  MFC 使用映射调用 [消息映射](../mfc/mapping-messages.md) 的特殊映射窗口消息为指向该消息的处理程序函数。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)
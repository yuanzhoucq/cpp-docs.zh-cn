---
title: 数组、 列表，并将类映射 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41dfe0b36548d87b5e0501c557e70f3cf11eea5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="array-list-and-map-classes"></a>数组、列表和映射类
为了处理数据的聚合，类库为集合类（数组、列表和映射）提供了一个组，该组可保留各种对象和预定义类型。 将动态调整集合的大小。 这些类可在任何程序中使用，无论是否为 Windows 编写的都是如此。 但是，它们对实现数据结构（定义应用程序框架中的文档类）最有用。 您可以轻松地从其中派生专用集合类，还可以基于模板类进行创建。 有关这些方法的详细信息，请参阅文章[集合](../mfc/collections.md)。 有关模板集合类的列表，请参阅文章[数组、 列表和映射的模板类](../mfc/template-classes-for-arrays-lists-and-maps.md)。  
  
 数组是连续存储在内存中的一维数据结构。 它们支持非常快的随机访问，因为任何给定元素的内存地址都可以通过将元素的索引乘以元素的大小并将结果添加到数组的基址来计算。 但是数组在您必须将元素插入数组时非常贵，因为插入元素的数组必须移动以为要插入的元素提供空间。 数组可根据需要增长和收缩。  
  
 列表类似于数组，但其存储方式截然不同。 列表中的每个元素还包括指向上一个元素和下一个元素的指针，这使列表像双重链接列表。 项目的添加或删除非常快，因为这样做仅涉及更改一些指针。 但是，搜索列表可能非常贵，因为所有搜索都需要在列表结尾之一处启动。  
  
 映射将一个键值与一个数据值相关联。 例如，映射的键可以是字符串和指针指向的列表数据。 您将要求映射为您提供与特殊字符串关联的指针。 映射查找非常快，因为映射将使用哈希表进行键查找。 项目的添加和删除也非常快。 映射通常与作为辅助索引的其他数据结构一起使用。 MFC 使用一种特殊的映射调用[消息映射](../mfc/mapping-messages.md)将 Windows 消息映射到指向该消息的处理程序函数的指针。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)


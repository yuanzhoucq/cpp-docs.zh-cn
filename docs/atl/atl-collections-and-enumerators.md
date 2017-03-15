---
title: "ATL 集合和枚举数 | Microsoft Docs"
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
  - "集合接口"
  - "集合, ATL 类"
  - "枚举器接口"
  - "枚举数, ATL 类"
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ATL 集合和枚举数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`collection` 是一个接口允许与数据项的COM对象\(原始数据或其他对象\)的一个组的访问。  按照提供的访问标准对于将一组对象的接口称为的 *集合接口*。  
  
 至少，集合接口必须提供返回的项数。集合、 **Item** 属性返回一个项目基于索引的集合和 `_NewEnum` 属性的返回集合的枚举数的 **Count** 属性。  或者，集合接口可以提供 **Add** 和 **Remove** 方法允许项插入到或从集合中删除和 **Clear** 方法移除所有项。  
  
 `enumerator` 是用于重复提供一个接口通过集合中的项的COM对象。  枚举器接口通过四个必需的方法提供序列化访问对于集合的元素: `Next`、 **Skip**、 **Reset**和 `Clone`。  
  
 通过了解详细了解枚举器接口原始模型（不过，完全名为）[IEnumXXXX](https://msdn.microsoft.com/en-us/library/ms680089.aspx)接口。  
  
## 本节内容  
 [ATL 集合和枚举数选件类](../atl/atl-collection-and-enumerator-classes.md)  
 简要描述并提供指向可帮助您实现集合和枚举数的ATL选件类。  
  
 [集合和枚举器接口的设计原则](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 讨论在接口后的每种不同的设计原则。  
  
 [实现基于STL的集合](../atl/implementing-an-stl-based-collection.md)  
 通过标准模板库遵循您\(STL\)基于集合的实现的扩展示例。  
  
## 相关章节  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 使用活动模板库提供一些链接，指向有关概念性主题有关如何使用进行编程。  
  
 [ATLCollections示例](../top/visual-cpp-samples.md)  
 演示如何使用 `ICollectionOnSTLImpl` 和 `CComEnumOnSTL`的示例和自定义复制策略类的实现。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)
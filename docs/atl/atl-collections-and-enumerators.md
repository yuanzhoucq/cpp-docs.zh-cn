---
title: ATL 集合和枚举数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 537d7e8b7264beddc68805ab8b8dec2ce7883859
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="atl-collections-and-enumerators"></a>ATL 集合和枚举数
A`collection`是提供一个允许对一组数据项 （原始数据或其他对象） 的访问接口的 COM 对象。 一个接口，用于提供对一组对象的访问被称为遵循标准*集合接口*。  
  
 集合接口必须提供至少**计数**属性在集合中，返回的项数**项**从基于索引的集合返回一个项的属性和`_NewEnum`返回集合的枚举数的属性。 或者，可提供的集合接口**添加**和**删除**方法以允许项要插入或删除集合中的属性和**清除**方法移除所有项。  
  
 `enumerator`是提供一个用于循环访问集合中的项接口的 COM 对象。 枚举器接口提供对通过四个所需的方法的集合的元素的串行访问： `Next`，**跳过**，**重置**，和`Clone`。  
  
 可以了解有关枚举器接口的详细信息，请参阅典型 （但完全虚部） [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)接口。  
  
## <a name="in-this-section"></a>本节内容  
 [ATL 集合和枚举器类](../atl/atl-collection-and-enumerator-classes.md)  
 简要介绍并提供指向 ATL 类，可帮助您实现集合和枚举数。  
  
 [集合和枚举器接口的设计原则](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 讨论每种类型的接口背后的不同的设计原则。  
  
 [实现基于 C++ 标准库的集合](../atl/implementing-an-stl-based-collection.md)  
 一个扩展的示例将指导你完成一个基于 c + + 标准库的集合的实现。  
  
## <a name="related-sections"></a>相关章节  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。  
  
 [ATLCollections 示例](../visual-cpp-samples.md)  
 一个示例，演示如何使用`ICollectionOnSTLImpl`和`CComEnumOnSTL`，和自定义复制策略类实现。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)


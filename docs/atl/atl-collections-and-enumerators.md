---
title: ATL 集合和枚举数
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 502bedb1773dc2a6edbd6679d50e9c5946228283
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491905"
---
# <a name="atl-collections-and-enumerators"></a>ATL 集合和枚举数

`collection`是一个 COM 对象, 它提供了一个接口, 该接口允许访问一组数据项 (原始数据或其他对象)。 遵循提供对一组对象的访问的标准的接口称为*集合接口*。

集合接口至少必须提供一个`Count`属性, 该属性可返回集合中的项的数目`Item` , 该属性根据索引从集合返回一个项, 并`_NewEnum`返回一个属性, 该属性返回集合的枚举器。 (可选) 集合接口可以`Add`提供`Remove`和方法, 以允许在集合中插入或删除项, 使用`Clear`方法可以移除所有项。

`enumerator`是一个 COM 对象, 它提供用于循环访问集合中的项的接口。 枚举器接口通过四个所需的方法, 提供对集合的元素`Next`的`Skip`串行访问: `Clone`、、 `Reset`和。

可以通过读取引用内容 (如[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring)接口) 来了解有关枚举器接口的详细信息。

## <a name="in-this-section"></a>本节内容

[ATL 集合和枚举器类](../atl/atl-collection-and-enumerator-classes.md)<br/>
简要描述并提供指向 ATL 类的链接, 它们可帮助您实现集合和枚举器。

[集合和枚举器接口的设计原则](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
讨论每种接口的各种设计原则。

[实现基于 C++ 标准库的集合](../atl/implementing-an-stl-based-collection.md)<br/>
一个扩展示例, 指导你完成基于库的C++标准集合的实现。

## <a name="related-sections"></a>相关章节

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

[ATLCollections 示例](../overview/visual-cpp-samples.md)<br/>
演示如何使用`ICollectionOnSTLImpl`和`CComEnumOnSTL`的示例, 以及如何实现自定义复制策略类。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)

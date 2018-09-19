---
title: ATL 集合和枚举器 |Microsoft Docs
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
ms.openlocfilehash: 4da59a76ccc4d51e82fd43805daa73d513fcde17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044270"
---
# <a name="atl-collections-and-enumerators"></a>ATL 集合和枚举数

一个`collection`是提供一个允许对一组数据 （原始数据或其他对象） 的项的访问接口的 COM 对象。 为提供对一组对象的访问被称为遵循标准的接口*集合接口*。

集合接口必须提供至少`Count`属性，用于在集合中，返回的项数`Item`从基于索引的集合返回一个项的属性和一个`_NewEnum`返回的属性集合的枚举器。 （可选） 可以提供集合接口`Add`和`Remove`方法以允许要插入到或从集合中删除项和一个`Clear`方法中删除所有项。

`enumerator`是一个用于遍历集合中的项提供一个接口的 COM 对象。 枚举器接口提供串行访问通过四个所需的方法集合的元素： `Next`， `Skip`， `Reset`，和`Clone`。

你可以了解有关通过阅读的枚举器接口的详细信息如参考内容[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)接口。

## <a name="in-this-section"></a>本节内容

[ATL 集合和枚举器类](../atl/atl-collection-and-enumerator-classes.md)<br/>
简要介绍并提供指向 ATL 类，这样有助于实现集合和枚举数。

[集合和枚举器接口的设计原则](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
讨论了每种类型的接口的不同的设计原则。

[实现基于 C++ 标准库的集合](../atl/implementing-an-stl-based-collection.md)<br/>
一个扩展的示例将指导你完成一个基于 c + + 标准库的集合的实现。

## <a name="related-sections"></a>相关章节

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

[ATLCollections 示例](../visual-cpp-samples.md)<br/>
一个示例，演示如何使用`ICollectionOnSTLImpl`和`CComEnumOnSTL`，和自定义复制策略类的实现。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)


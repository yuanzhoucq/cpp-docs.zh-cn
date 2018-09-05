---
title: 实现 CComObject、 CComAggObject 和 CComPolyObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs:
- C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 815edfa733e828169404258694133ffa0031917a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755571"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>实现 CComObject、 CComAggObject 和 CComPolyObject

模板类[CComObject](../atl/reference/ccomobject-class.md)， [CComAggObject](../atl/reference/ccomaggobject-class.md)，并[CComPolyObject](../atl/reference/ccompolyobject-class.md)始终是继承链中的派生程度最大的类。 它们来处理所有中的方法有责任`IUnknown`: `QueryInterface`， `AddRef`，和`Release`。 此外，`CComAggObject`并`CComPolyObject`（当使用聚合对象） 提供特殊的引用计数和`QueryInterface`所需的内部未知的语义。

是否`CComObject`， `CComAggObject`，或`CComPolyObject`使用取决于您声明一个 （或无） 以下宏：

|宏|效果|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|始终使用`CComObject`。|
|DECLARE_AGGREGATABLE|使用`CComAggObject`如果该对象进行了聚合和`CComObject`如果不是。 `CComCoClass` 包含此宏，如果没有 DECLARE_ * _AGGREGATABLE 宏声明在类中，这将是默认值。|
|DECLARE_ONLY_AGGREGATABLE|始终使用`CComAggObject`。 如果该对象不会聚合，则返回错误。|
|DECLARE_POLY_AGGREGATABLE|ATL 创建的实例**CComPolyObject\<CYourClass >** 时`IClassFactory::CreateInstance`调用。 在创建期间，检查外部未知的值。 如果值为 NULL，`IUnknown`为非聚合对象实现。 如果未知的外部不为 NULL，`IUnknown`为聚合对象实现。|

使用的优点`CComAggObject`并`CComObject`在于实现`IUnknown`针对所创建对象的类型进行了优化。 例如，非聚合的对象只需引用计数，而聚合的对象需要内部未知的引用计数和未知的外部的指针。

使用的优点`CComPolyObject`避免同时`CComAggObject`和`CComObject`处理聚合和非聚合的情况下在模块中。 单个`CComPolyObject`对象将处理这两种情况。 这意味着你的模块中存在的 vtable 只有一个副本和函数的一个副本。 如果你 vtable 很大，这可以显著减少模块大小。 但是，如果你 vtable 很小，则使用`CComPolyObject`可能导致稍大模块大小，因为它不优化聚合或非聚合对象，因为`CComAggObject`和`CComObject`。

## <a name="see-also"></a>请参阅

[ATL COM 对象的基础知识](../atl/fundamentals-of-atl-com-objects.md)   
[聚合和类工厂宏](../atl/reference/aggregation-and-class-factory-macros.md)


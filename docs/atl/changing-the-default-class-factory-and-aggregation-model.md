---
title: 更改默认类工厂和聚合模型
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: 1c97d8f63a441fab2b76c6e0509e4b3f384308ea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220881"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>更改默认类工厂和聚合模型

ATL 使用[CComCoClass](../atl/reference/ccomcoclass-class.md)定义对象的默认类工厂和聚合模型。 `CComCoClass`指定下面两个宏：

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory)声明要[CComClassFactory](../atl/reference/ccomclassfactory-class.md)的类工厂。

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable)声明可以聚合您的对象。

您可以通过在类定义中指定另一个宏来重写这些默认值之一。 例如，若要使用[CComClassFactory2](../atl/reference/ccomclassfactory2-class.md)而不是 `CComClassFactory` ，请指定[DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2)宏：

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

定义类工厂的其他两个宏是[DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)和[DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton)。

ATL 还使用 **`typedef`** 机制来实现默认行为。 例如，DECLARE_AGGREGATABLE 宏使用 **`typedef`** 定义名为的类型 `_CreatorClass` ，然后在整个 ATL 中引用该类型。 请注意，在派生类中， **`typedef`** 使用与基类相同的名称，将 **`typedef`** 使用您的定义生成 ATL，并覆盖默认行为。

## <a name="see-also"></a>另请参阅

[ATL COM 对象的基本知识](../atl/fundamentals-of-atl-com-objects.md)<br/>
[聚合和类工厂宏](../atl/reference/aggregation-and-class-factory-macros.md)

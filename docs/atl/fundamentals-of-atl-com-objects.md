---
title: ATL COM 对象的基础知识 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b90d8901a60b5945b2b29db2c378a0cd29939f63
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059261"
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 对象的基础知识

下图描绘了类和接口，用于定义 ATL COM 对象之间的关系。

![ATL 结构](../atl/media/vc307y1.gif "vc307y1")

> [!NOTE]
>  此图`CComObject`派生自`CYourClass`而`CComAggObject`并`CComPolyObject`包括`CYourClass`作为成员变量。

有三种方法来定义 ATL COM 对象。 标准做法是使用`CComObject`类，该类派生自`CYourClass`。 第二个选项是通过使用创建聚合的对象`CComAggObject`类。 第三个选项是使用`CComPolyObject`类。 `CComPolyObject` 充当混合： 它可以用作`CComObject`类或`CComAggObject`类，具体取决于如何首次创建。 有关如何使用详细信息`CComPolyObject`类，请参阅[CComPolyObject 类](../atl/reference/ccompolyobject-class.md)。

当使用标准的 ATL COM 时，使用两个对象： 外部对象和一个内部对象。 外部客户端通过在外部对象中定义的包装器函数访问内部对象的功能。 外部对象属于类型`CComObject`。

时使用的聚合的对象，外层对象不提供的功能的内部对象包装器。 相反，外层对象提供了由外部客户端直接访问的指针。 在此方案中，外层对象属于类型`CComAggObject`。 内部对象的外部对象的成员变量，它是类型的`CYourClass`。

因为客户端不具有为通过外部对象能够与内部对象进行交互，聚合的对象是通常更高效。 此外，外层对象无需知道功能的聚合的对象，聚合对象的接口是直接提供给客户端。 但是，并非所有对象可进行都聚合。 要聚合的对象，它需要记住的聚合设计。

ATL 实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)分两个阶段：

- [CComObject](../atl/reference/ccomobject-class.md)， [CComAggObject](../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../atl/reference/ccompolyobject-class.md)实现`IUnknown`方法。

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理的引用计数和外部的指针`IUnknown`。

ATL COM 对象的其他方面由其他类处理：

- [CComCoClass](../atl/reference/ccomcoclass-class.md)定义对象的默认类工厂和聚合模型。

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的默认实现`IDispatch Interface`对象上的任何双接口的一部分。

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)实现`ISupportErrorInfo`接口，可确保错误信息可以在调用链正确传播。

## <a name="in-this-section"></a>本节内容

[实现 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
显示用于实现的 COM 映射条目的示例`CComObjectRootEx`。

[实现 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
讨论如何**DECLARE_\*_AGGREGATABLE**宏会影响使用`CComObject`， `CComAggObject`，并`CComPolyObject`。

[支持 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
列出了用于支持的 ATL 实现类`IDispatch`和`IErrorInfo`接口。

[支持 IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
讨论了实现您的类的连接点的步骤。

[更改默认类工厂和聚合模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
显示哪些宏，以使用更改默认类工厂和聚合模型。

[创建聚合对象](../atl/creating-an-aggregated-object.md)<br/>
列出了用于创建聚合的对象的步骤。

## <a name="related-sections"></a>相关章节

[创建 ATL 项目](../atl/reference/creating-an-atl-project.md)<br/>
提供有关创建 ATL COM 对象的信息。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)


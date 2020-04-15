---
title: ATL COM 对象的基础知识
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319561"
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 对象的基础知识

下图描述了用于定义 ATL COM 对象的类和接口之间的关系。

![ATL 结构](../atl/media/vc307y1.gif "ATL 结构")

> [!NOTE]
> 此图显示`CComObject`派生自`CYourClass`而`CComAggObject`并作为`CComPolyObject`成员变量包含`CYourClass`的函数。

有三种方法可以定义 ATL COM 对象。 标准选项是使用派生自`CComObject``CYourClass`的类。 第二个选项是使用 类`CComAggObject`创建聚合对象。 第三个选项是使用 类`CComPolyObject`。 `CComPolyObject`充当混合体：它可以作为类`CComObject`或`CComAggObject`类运行，具体取决于它最初创建的方式。 有关如何使用类的详细信息，`CComPolyObject`请参阅[CComPolyObject 类](../atl/reference/ccompolyobject-class.md)。

使用标准 ATL COM 时，可以使用两个对象：外部对象和内部对象。 外部客户端通过外部对象中定义的包装函数访问内部对象的功能。 外部对象的类型`CComObject`为 。

使用聚合对象时，外部对象不为内部对象的功能提供包装器。 相反，外部对象提供外部客户端直接访问的指针。 在这种情况下，外部对象的类型`CComAggObject`为 。 内部对象是外部对象的成员变量，它是 类型`CYourClass`。

由于客户端不必通过外部对象与内部对象交互，因此聚合对象通常效率更高。 此外，外部对象不必知道聚合对象的功能，因为聚合对象的接口直接可供客户端使用。 但是，并非所有对象都可以聚合。 要聚合对象，需要考虑到聚合来设计它。

ATL 分两个阶段实现[I 未知：](/windows/win32/api/unknwn/nn-unknwn-iunknown)

- [CComObject](../atl/reference/ccomobject-class.md)CComObject、CComAggObject 或[CComPolyObject](../atl/reference/ccompolyobject-class.md) `IUnknown`实现这些方法。 [CComAggObject](../atl/reference/ccomaggobject-class.md)

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理 的`IUnknown`引用计数和外部指针。

ATL COM 对象的其他方面由其他类处理：

- [CComCoClass](../atl/reference/ccomcoclass-class.md)定义对象的默认类工厂和聚合模型。

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供对象上任何双`IDispatch Interface`接口部分的默认实现。

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)实现了`ISupportErrorInfo`确保错误信息可以正确传播到呼叫链上的接口。

## <a name="in-this-section"></a>本节内容

[实现 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
显示实现`CComObjectRootEx`的 COM 映射条目示例。

[实现 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
讨论**DECLARE__AGGREGATABLE\*** 宏如何影响`CComObject``CComAggObject`和 的使用`CComPolyObject`。

[支持 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
列出用于支持 和`IDispatch``IErrorInfo`接口的 ATL 实现类。

[支持 IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
讨论实现类连接点的步骤。

[更改默认类工厂和聚合模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
显示用于更改默认类工厂和聚合模型的宏。

[创建聚合对象](../atl/creating-an-aggregated-object.md)<br/>
列出创建聚合对象的步骤。

## <a name="related-sections"></a>相关章节

[创建 ATL 项目](../atl/reference/creating-an-atl-project.md)<br/>
提供有关创建 ATL COM 对象的信息。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

## <a name="see-also"></a>另请参阅

[概念](../atl/active-template-library-atl-concepts.md)

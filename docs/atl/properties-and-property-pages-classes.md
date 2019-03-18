---
title: 属性和属性页类 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: 05c3a67e278389bb2ab1b07e9d6cf63cbe347c63
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57807512"
---
# <a name="properties-and-property-pages-classes"></a>属性和属性页类

以下类支持的属性和属性页：

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver)检索或设置对象的属性通过`IDispatch`指针。

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md)实现 atl。 支持的常用属性

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md)访问对象的属性页中的信息。

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md)客户端提供的属性包中存储对象的属性。

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md)管理属性表中的特定属性页面。

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md)类似于`IPropertyPageImpl`，但还允许客户端在属性页中选择的特定属性。

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)获取支持的对象的属性页的 Clsid。

## <a name="related-articles"></a>相关文章

[ATL 教程](../atl/active-template-library-atl-tutorial.md)

[ATL COM 属性页](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)<br/>
[属性映射宏](../atl/reference/property-map-macros.md)

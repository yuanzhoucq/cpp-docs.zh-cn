---
title: 枚举器和集合类 (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.enum
helpviewer_keywords:
- enumerators, ATL classes
ms.assetid: fcd093b2-98bf-444d-94ab-9a55520a5051
ms.openlocfilehash: 537dd14a02de6686a8db1e3a0d88983b8bb3cc34
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263490"
---
# <a name="enumerators-and-collections-classes"></a>枚举器和集合类

以下类提供支持 COM 集合和枚举：

- [CComEnum](../atl/reference/ccomenum-class.md)定义 COM 枚举器对象基于数组。

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)提供要枚举的项数组中的存储位置的 COM 枚举器接口的实现。

- [CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)定义 COM 枚举器对象，基于 c + + 标准库集合。

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)提供要枚举的项在兼容的 c + + 标准库容器中的存储位置的 COM 枚举器接口的实现。

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)提供了用于实现`Count`， `Item`，和`_NewEnum`集合接口的属性。

## <a name="related-articles"></a>相关文章

[ATL 集合和枚举数](../atl/atl-collections-and-enumerators.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)

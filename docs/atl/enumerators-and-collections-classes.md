---
title: 枚举器和集合类 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerators, ATL classes
ms.assetid: fcd093b2-98bf-444d-94ab-9a55520a5051
ms.openlocfilehash: 6de81a7b0ddd77471669b19c4be1145c776d2902
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2019
ms.locfileid: "57809803"
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

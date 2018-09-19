---
title: 枚举器和集合类 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.enum
dev_langs:
- C++
helpviewer_keywords:
- enumerators, ATL classes
ms.assetid: fcd093b2-98bf-444d-94ab-9a55520a5051
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c84becc5b7117c9095a055e6a815e52396987800
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758386"
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


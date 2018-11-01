---
title: ATL 集合和枚举器类
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: a0d7483cc142377ec4de903e27f23056a9e8dd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495296"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 集合和枚举器类

ATL 提供了以下类来帮助你实现集合和枚举数。

|类|描述|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合接口实现|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|枚举器接口实现 （假定兼容的 c + + 标准库容器中存储的数据）|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|枚举器接口实现 （假定数组中存储的数据）|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|枚举器对象实现 (使用`IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|枚举器对象实现 (使用`CComEnumImpl`)|
|[（_c)](../atl/atl-copy-policy-classes.md)|复制策略类|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|复制策略类|
|[CAdapt](../atl/reference/cadapt-class.md)|适配器类 (隐藏**运算符 &** 允许`CComPtr`， `CComQIPtr`，和`CComBSTR`要存储在 c + + 标准库容器中)|

## <a name="see-also"></a>请参阅

[集合和枚举数](../atl/atl-collections-and-enumerators.md)


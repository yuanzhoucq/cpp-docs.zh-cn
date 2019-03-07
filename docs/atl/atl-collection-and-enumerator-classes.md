---
title: ATL 集合和枚举器类
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265400"
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
|[_Copy](../atl/atl-copy-policy-classes.md)|复制策略类|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|复制策略类|
|[CAdapt](../atl/reference/cadapt-class.md)|适配器类 (隐藏**运算符 &** 允许`CComPtr`， `CComQIPtr`，和`CComBSTR`要存储在 c + + 标准库容器中)|

## <a name="see-also"></a>请参阅

[集合和枚举数](../atl/atl-collections-and-enumerators.md)

---
title: ATL 集合和枚举器类
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252320"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 集合和枚举器类

ATL 提供了以下类来帮助你实现集合和枚举数。

|类|描述|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合接口实现|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|枚举器接口实现 (假定数据存储在C++标准库兼容容器)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|枚举器接口实现 （假定数组中存储的数据）|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|枚举器对象实现 (使用`IEnumOnSTLImpl`)|
|[CComEnum](../atl/reference/ccomenum-class.md)|枚举器对象实现 (使用`CComEnumImpl`)|
|[_Copy](../atl/atl-copy-policy-classes.md)|复制策略类|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|复制策略类|
|[CAdapt](../atl/reference/cadapt-class.md)|适配器类 (隐藏**运算符 &** 允许`CComPtr`， `CComQIPtr`，并`CComBSTR`存储在C++标准库容器)|

## <a name="see-also"></a>请参阅

[集合和枚举数](../atl/atl-collections-and-enumerators.md)

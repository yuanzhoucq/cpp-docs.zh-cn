---
title: ATL 集合和枚举器类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0ff5fec4749e08826bab5572149c6cd24a204f9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765068"
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


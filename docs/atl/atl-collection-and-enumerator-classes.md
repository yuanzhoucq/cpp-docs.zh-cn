---
title: ATL 集合和枚举器类 |Microsoft 文档
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
ms.openlocfilehash: a47525bb21b896b0fef8393cab66142ed40311ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354441"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 集合和枚举器类
ATL 提供的以下类，可帮助你实现集合和枚举数。  
  
|类|描述|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合接口实现|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|枚举器接口的实现 （假定兼容的 c + + 标准库容器中存储的数据）|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|枚举器接口的实现 （假设存储在数组中的数据）|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|枚举器对象实现 (使用`IEnumOnSTLImpl`)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|枚举器对象实现 (使用`CComEnumImpl`)|  
|[_Copy](../atl/atl-copy-policy-classes.md)|复制策略类|  
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|复制策略类|  
|[CAdapt](../atl/reference/cadapt-class.md)|适配器类 (隐藏**运算符 （& a)** 允许`CComPtr`， `CComQIPtr`，和`CComBSTR`要存储在 c + + 标准库容器中)|  
  
## <a name="see-also"></a>请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)


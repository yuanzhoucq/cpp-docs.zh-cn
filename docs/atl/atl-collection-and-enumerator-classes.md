---
title: "ATL 集合和枚举器类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fe6a018668f40c632e0ff980499afb7e60de8ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
|[CAdapt](../atl/reference/cadapt-class.md)|适配器类 (隐藏**运算符 （& a)**允许`CComPtr`， `CComQIPtr`，和`CComBSTR`要存储在 c + + 标准库容器中)|  
  
## <a name="see-also"></a>另请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)


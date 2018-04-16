---
title: "CSimpleArrayEqualHelperFalse 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28d43b6a83842373c2fc169ce43022f1912c4e0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse 类
此类是帮助器[CSimpleArray](../../atl/reference/csimplearray-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 派生的类。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|（静态）返回 false。|  
  
## <a name="remarks"></a>备注  
 此特征类是对补充`CSimpleArray`类。 It 始终返回 false，和此外，将调用`ATLASSERT`用 false 如果曾引用自变量。 在其中相等性测试未充分定义的情况下，此类允许包含要正确运行的大多数方法，但如依赖于比较的方法定义完善的方式失败元素数组[CSimpleArray::查找](../../atl/reference/csimplearray-class.md#find)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual  
 返回 false。  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>返回值  
 返回 false。  
  
### <a name="remarks"></a>备注  
 此方法始终返回 false，并且将调用`ATLASSERT`用 false 如果引用自变量。 用途`CSimpleArrayEqualHelperFalse::IsEqual`是强制使用比较时没有充分定义相等性测试，以定义完善的方式失败的方法。  
  
## <a name="see-also"></a>请参阅  
 [CSimpleArrayEqualHelper 类](../../atl/reference/csimplearrayequalhelper-class.md)   
 [类概述](../../atl/atl-class-overview.md)

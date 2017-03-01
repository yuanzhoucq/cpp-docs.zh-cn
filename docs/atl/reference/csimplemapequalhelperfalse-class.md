---
title: "CSimpleMapEqualHelperFalse 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CSimpleMapEqualHelperFalse
- CSimpleMapEqualHelperFalse
- ATL.CSimpleMapEqualHelperFalse
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 68a08ffc0ba126c523a779e3d1a72217dead6235
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 类
此类是帮助器[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|（静态）测试两个键相等。|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|（静态）返回 false。|  
  
## <a name="remarks"></a>备注  
 此特征类是对的补充`CSimpleMap`类。 它提供了一种方法比较两个元素中包含`CSimpleMap`对象，特别是两个值的元素或两个关键元素。  
  
 值比较将始终返回 false，并且另外，将调用`ATLASSERT`参数为 false，如果它曾经引用。 在相等性测试不充分定义的位置的情况下，此类允许包含键/值对大多数方法正常运行，但失败，如依赖比较的方法的定义完善的方式映射[CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpcoll.h  
  
##  <a name="a-nameisequalkeya--csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey  
 测试两个键相等。  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>参数  
 `k1`  
 第一个键。  
  
 `k2`  
 第二个键。  
  
### <a name="return-value"></a>返回值  
 如果键相等，则返回 false 否则，则返回 true。  
  
### <a name="remarks"></a>备注  
 此方法调用[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)。  
  
##  <a name="a-nameisequalvaluea--csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue  
 返回 false。  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>返回值  
 返回 false。  
  
### <a name="remarks"></a>备注  
 此方法始终返回 false，并且将调用`ATLASSERT`参数为 false，如果它曾经引用。 用途`CSimpleMapEqualHelperFalse::IsEqualValue`是强制方法使用比较时尚未充分定义相等性测试，以定义完善的方式失败。  
  
## <a name="see-also"></a>另请参阅  
 [CSimpleMapEqualHelper 类](../../atl/reference/csimplemapequalhelper-class.md)   
 [类概述](../../atl/atl-class-overview.md)


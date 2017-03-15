---
title: "CSimpleArrayEqualHelperFalse 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CSimpleArrayEqualHelperFalse<T>
- ATL::CSimpleArrayEqualHelperFalse
- ATL.CSimpleArrayEqualHelperFalse
- ATL::CSimpleArrayEqualHelperFalse<T>
- CSimpleArrayEqualHelperFalse
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
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
ms.openlocfilehash: cd5ed7058194880ef1ceaebe788e3deb60d4ac8e
ms.lasthandoff: 02/24/2017

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
 派生的类中。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|（静态）返回 false。|  
  
## <a name="remarks"></a>备注  
 此特征类是对补充`CSimpleArray`类。 It 始终返回 false，，此外，将拨`ATLASSERT`参数为 false，如果它曾经引用。 在相等性测试不充分定义的位置的情况下，此类允许数组，其中包含元素，对于大多数方法正常运行，但如依赖比较的方法的定义完善的方式失败[CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpcoll.h  
  
##  <a name="a-nameisequala--csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual  
 返回 false。  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>返回值  
 返回 false。  
  
### <a name="remarks"></a>备注  
 此方法始终返回 false，并且将调用`ATLASSERT`false 如果引用的参数。 用途`CSimpleArrayEqualHelperFalse::IsEqual`是强制方法使用比较时尚未充分定义相等性测试，以定义完善的方式失败。  
  
## <a name="see-also"></a>另请参阅  
 [CSimpleArrayEqualHelper 类](../../atl/reference/csimplearrayequalhelper-class.md)   
 [类概述](../../atl/atl-class-overview.md)


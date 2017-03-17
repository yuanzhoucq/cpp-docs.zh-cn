---
title: "CSimpleArrayEqualHelper 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4a87879683257c66de5fe4e720dd29fa4c47031d
ms.lasthandoff: 02/24/2017

---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper 类
此类是帮助器[CSimpleArray](../../atl/reference/csimplearray-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 派生的类中。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|（静态）测试两个`CSimpleArray`对象是否相等的元素。|  
  
## <a name="remarks"></a>备注  
 此特征类是对的补充`CSimpleArray`类。 它提供了一种方法，用于比较两个元素存储在`CSimpleArray`对象。 默认情况下，对元素进行比较使用**operator=()**，但如果该数组包含缺少他们自己的相等运算符的复杂数据类型，您将需要重写此类。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
 测试两个`CSimpleArray`对象是否相等的元素。  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>参数  
 *t1*  
 一个对象类型为 t。  
  
 *t2*  
 一个对象类型为 t。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
## <a name="see-also"></a>另请参阅  
 [CSimpleArray 类](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse 类](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [类概述](../../atl/atl-class-overview.md)


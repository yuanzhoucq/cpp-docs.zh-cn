---
title: "CPrimitiveElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
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
ms.openlocfilehash: 44e3849ebf2de09bc9b62e28df0f70bf52ac95e6
ms.lasthandoff: 02/24/2017

---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits 类
此类提供了默认的方法和函数的集合类构成的基元数据类型。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 集合类对象中存储的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
## <a name="remarks"></a>备注  
 此类提供默认静态函数和移动、 复制、 比较和哈希存储在集合类对象中的基元数据类型元素的方法。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CPrimitiveElementTraits`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef T INARGTYPE;
```  
  
##  <a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE  
 要用于从集合类对象中检索元素的数据类型。  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另请参阅  
 [CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)


---
title: "CDefaultCompareTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
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
ms.openlocfilehash: 1d1253b7a7d69024465627cc9fb37fcd2afba693
ms.lasthandoff: 02/24/2017

---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 类
此类提供了默认元素比较函数。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CDefaultCompareTraits
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要在集合中存储的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](#compareelements)|（静态）调用此函数可比较两个元素相等。|  
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|（静态）调用此函数可确定更高版本或更低的元素。|  
  
## <a name="remarks"></a>备注  
 此类包含用于存储在集合类对象中的元素进行比较的两个静态函数。 此类利用[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="compareelements"></a>CDefaultCompareTraits::CompareElements  
 调用此函数可比较两个元素相等。  
  
```
static bool CompareElements(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>参数  
 `element1`  
 第一个元素。  
  
 `element2`  
 第二个元素。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现是等号 ( `==`) 运算符。 对于以外的简单数据类型的对象，该函数可能需要重写。  
  
##  <a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered  
 调用此函数可确定更高版本或更低的元素。  
  
```
static int CompareElementsOrdered(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>参数  
 `element1`  
 第一个元素。  
  
 `element2`  
 第二个元素。  
  
### <a name="return-value"></a>返回值  
 返回一个整数，基于以下表︰  
  
|条件|返回值|  
|---------------|------------------|  
|`element1` < `element2`|<0|  
|`element1` == `element2`|0|  
|`element1` > `element2`|>0|  
  
### <a name="remarks"></a>备注  
 此函数的默认实现使用`==`， ** \< **，和** > **运算符。 对于以外的简单数据类型的对象，该函数可能需要重写。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)


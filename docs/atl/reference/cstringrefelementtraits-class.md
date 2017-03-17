---
title: "CStringRefElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
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
ms.openlocfilehash: 3709a5d4aac02651e5b6fafd441499fea1f8eabc
ms.lasthandoff: 02/24/2017

---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits 类
此类提供与存储在集合类对象的字符串相关的静态函数。 字符串对象作为引用的处理。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要在集合中存储的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|调用该静态函数用于比较两个字符串元素相等。|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|调用该静态函数用于比较两个字符串元素。|  
|[CStringRefElementTraits::Hash](#hash)|调用该静态函数来计算给定的字符串元素进行哈希值。|  
  
## <a name="remarks"></a>备注  
 此类提供静态函数用于比较字符串和用于创建哈希值。 使用集合类来存储基于字符串的数据时，这些函数很有用。 与不同[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)，`CStringRefElementTraits`导致`CString`参数作为传递**const CString &**引用。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="compareelements"></a>CStringRefElementTraits::CompareElements  
 调用该静态函数用于比较两个字符串元素相等。  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>参数  
 `element1`  
 第一个字符串元素。  
  
 `element2`  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
##  <a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered  
 调用该静态函数用于比较两个字符串元素。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串元素。  
  
 `str2`  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果字符串是相同的则为零< 0="" if="">`str1`是小于`str2`，则为 0 1> 如果`str1`大于`str2`。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。  
  
##  <a name="hash"></a>CStringRefElementTraits::Hash  
 调用该静态函数来计算给定的字符串元素进行哈希值。  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>参数  
 `str`  
 字符串元素中。  
  
### <a name="return-value"></a>返回值  
 返回使用字符串的内容来计算哈希值。  
  
## <a name="see-also"></a>另请参阅  
 [CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)   
 [类概述](../../atl/atl-class-overview.md)


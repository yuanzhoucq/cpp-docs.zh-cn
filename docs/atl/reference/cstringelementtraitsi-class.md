---
title: "CStringElementTraitsI 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CStringElementTraitsI
- CStringElementTraitsI
- ATL.CStringElementTraitsI
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: 18
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
ms.openlocfilehash: 995c4798f92db3b3f065bf2176ab52ff53d282b0
ms.lasthandoff: 02/24/2017

---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI 类
此类提供与存储在集合类对象的字符串相关的静态函数。 它相当于[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但执行不区分大小写的比较。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>  
class CStringElementTraitsI : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要在集合中存储的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](#compareelements)|调用该静态函数以比较两个字符串元素相等性，忽略大小写差异。|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|调用该静态函数用于比较两个字符串元素，忽略大小写差异。|  
|[CStringElementTraitsI::Hash](#hash)|调用该静态函数来计算给定的字符串元素进行哈希值。|  
  
## <a name="remarks"></a>备注  
 此类提供静态函数用于比较字符串和用于创建哈希值。 使用集合类来存储基于字符串的数据时，这些函数很有用。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)与得到处理作为引用的字符串对象的时间。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="a-namecompareelementsa--cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::CompareElements  
 调用该静态函数以比较两个字符串元素相等性，忽略大小写差异。  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串元素。  
  
 `str2`  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
### <a name="remarks"></a>备注  
 比较是区分大小写。  
  
##  <a name="a-namecompareelementsordereda--cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered  
 调用该静态函数用于比较两个字符串元素，忽略大小写差异。  
  
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

  
### <a name="remarks"></a>备注  
 比较是区分大小写。  
  
##  <a name="a-namehasha--cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash  
 调用该静态函数来计算给定的字符串元素进行哈希值。  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>参数  
 `str`  
 字符串元素中。  
  
### <a name="return-value"></a>返回值  
 返回使用字符串的内容来计算哈希值。  
  
##  <a name="a-nameinargtypea--cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="a-nameoutargtypea--cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE  
 要用于从集合类对象中检索元素的数据类型。  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另请参阅  
 [CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CStringElementTraits 类](../../atl/reference/cstringelementtraits-class.md)


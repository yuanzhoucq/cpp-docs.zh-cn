---
title: CStringElementTraits 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0c6ed9fb68e685a7b8a59b049277e61f41fd2ce
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885720"
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 类
此类提供了使用的存储的集合类的静态函数`CString`对象。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 要存储在集合中的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|（静态）调用此函数用于比较相等的两个字符串元素。|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|（静态）调用此函数用于比较两个字符串元素。|  
|[CStringElementTraits::CopyElements](#copyelements)|（静态）调用此函数可将复制`CString`集合类对象中存储的元素。|  
|[CStringElementTraits::Hash](#hash)|（静态）调用此函数来计算给定的字符串元素的哈希值。|  
|[CStringElementTraits::RelocateElements](#relocateelements)|（静态）调用此函数可重新定位`CString`集合类对象中存储的元素。|  
  
## <a name="remarks"></a>备注  
 此类提供静态函数进行复制、 移动和比较字符串和用于创建哈希值。 使用集合类来存储基于字符串的数据时，这些函数很有用。 使用[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)需要不区分大小写比较时。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)字符串对象的引用作为在处理时。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** cstringt.h  
  
##  <a name="compareelements"></a>  CStringElementTraits::CompareElements  
 调用此静态函数以比较相等的两个字符串元素。  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>参数  
 *str1*  
 第一个字符串元素。  
  
 *str2*  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
##  <a name="compareelementsordered"></a>  CStringElementTraits::CompareElementsOrdered  
 调用此静态函数以比较两个字符串元素。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>参数  
 *str1*  
 第一个字符串元素。  
  
 *str2*  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果字符串相等则为零，< 0 如果*str1*是小于*str2*，或 > 0 如果*str1*大于*str2*。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。  

  
##  <a name="copyelements"></a>  CStringElementTraits::CopyElements  
 调用此静态函数以将复制`CString`集合类对象中存储的元素。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>参数  
 *pDest*  
 指向将接收复制的数据的第一个元素的指针。  
  
 *pSrc*  
 指向要复制的第一个元素的指针。  
  
 *nElements*  
 要复制的元素数。  
  
### <a name="remarks"></a>备注  
 不应重叠的源和目标元素。  
  
##  <a name="hash"></a>  CStringElementTraits::Hash  
 调用此静态函数以计算给定的字符串元素的哈希值。  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>参数  
 *str*  
 字符串元素中。  
  
### <a name="return-value"></a>返回值  
 返回使用字符串的内容计算的哈希值。  
  
##  <a name="inargtype"></a>  CStringElementTraits::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CStringElementTraits::OUTARGTYPE  
 要用于从集合类对象中检索元素的数据类型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>  CStringElementTraits::RelocateElements  
 调用此静态函数以重新定位`CString`集合类对象中存储的元素。  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>参数  
 *pDest*  
 指向将接收重新定位的数据的第一个元素的指针。  
  
 *pSrc*  
 指向要重新定位的第一个元素的指针。  
  
 *nElements*  
 要重新定位的元素数。  
  
### <a name="remarks"></a>备注  
 此静态函数将调用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，足以满足大多数数据类型。 如果要移动的对象包含指向其自己的成员的指针，将需要重写此静态函数。  
  
## <a name="see-also"></a>请参阅  
 [CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI 类](../../atl/reference/cstringelementtraitsi-class.md)   
 [类概述](../../atl/atl-class-overview.md)

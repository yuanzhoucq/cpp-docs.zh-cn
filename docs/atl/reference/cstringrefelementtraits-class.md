---
title: CStringRefElementTraits 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8746bf216be417fb569aae58421b272c983914b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360682"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits 类
此类提供与集合类对象中存储的字符串相关的静态函数。 字符串对象以引用的方式处理的。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合中的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|调用此静态函数以比较相等的两个字符串元素。|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|调用此静态函数以比较两个字符串元素。|  
|[CStringRefElementTraits::Hash](#hash)|调用此静态函数以计算给定的字符串元素的哈希值。|  
  
## <a name="remarks"></a>备注  
 此类提供静态函数用于比较字符串和用于创建哈希值。 使用的集合类来存储基于字符串的数据时，这些函数很有用。 与不同[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)，`CStringRefElementTraits`导致`CString`自变量作为传递**const CString &** 引用。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements  
 调用此静态函数以比较相等的两个字符串元素。  
  
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
  
##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered  
 调用此静态函数以比较两个字符串元素。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串元素。  
  
 `str2`  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 零; 如果字符串相同，则 < 0 如果`str1`是小于`str2`，或 > 0 如果`str1`大于`str2`。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。  
  
##  <a name="hash"></a>  CStringRefElementTraits::Hash  
 调用此静态函数以计算给定的字符串元素的哈希值。  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>参数  
 `str`  
 字符串元素中。  
  
### <a name="return-value"></a>返回值  
 返回一个哈希值，使用字符串的内容计算。  
  
## <a name="see-also"></a>请参阅  
 [CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)   
 [类概述](../../atl/atl-class-overview.md)

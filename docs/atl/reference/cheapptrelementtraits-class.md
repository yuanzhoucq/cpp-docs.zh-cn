---
title: "CHeapPtrElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: cf442a47a8f7f56a9563b73d03224165248232d5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits 类
此类提供方法、 静态函数和有用的 typedef 时创建的堆指针的集合。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合类的对象类型。  
  
 `Allocator`  
 要使用的内存分配类。 默认值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
## <a name="remarks"></a>备注  
 此类提供对帮助包含堆指针的集合类对象的创建方法、 静态函数和类型定义。 此类`CHeapPtrList`派生自`CHeapPtrElementTraits`。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="inargtype"></a>CHeapPtrElementTraits::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CHeapPtrElementTraits::OUTARGTYPE  
 要用于从集合类对象中检索元素的数据类型。  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另请参阅  
 [CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)   
 [CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)   
 [类概述](../../atl/atl-class-overview.md)


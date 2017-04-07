---
title: "CAutoPtrElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 1c543eaa678d86e083207915bcb4f43766ee23c5
ms.lasthandoff: 02/24/2017

---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits 类
此类提供方法、 静态函数和有用的 typedef 时创建的智能指针的集合。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CAutoPtrElementTraits 
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```    
  
#### <a name="parameters"></a>参数  
 `T`  
 指针类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
## <a name="remarks"></a>备注  
 此类提供对帮助包含智能指针的集合类对象的创建方法、 静态函数和类型定义。 这些类[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)派生自`CAutoPtrElementTraits`。 如果构建的智能指针集合需要新的矢量和 delete 运算符，可以使用[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)相反。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef CAutoPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE  
 要用于从集合类对象中检索元素的数据类型。  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另请参阅  
 [CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)


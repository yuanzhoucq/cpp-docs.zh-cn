---
title: "CAutoPtrElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs: C++
helpviewer_keywords: CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b1b7d09894e7258ab740e09fb45008a4eeb8a3ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits 类
此类提供方法、 静态函数和有用的 typedef 时创建的智能指针的集合。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|要用来检索元素的集合类对象的数据类型。|  
  
## <a name="remarks"></a>备注  
 此类提供对帮助创建包含智能指针集合类对象的方法、 静态函数和 typedef。 类[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)派生自`CAutoPtrElementTraits`。 如果生成，该服务的智能指针集合需要新的向量和 delete 运算符，使用[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)相反。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CAutoPtrElementTraits`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef CAutoPtr<T>& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE  
 要用来检索元素的集合类对象的数据类型。  
  
```
typedef T *& OUTARGTYPE;
```  
  
## <a name="see-also"></a>另请参阅  
 [CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)

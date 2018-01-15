---
title: "CAutoPtrArray 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs: C++
helpviewer_keywords: CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4afb07323cdb6b25914aabd802c4df73ee1d07c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 类
构造的智能指针的数组时，此类提供有用的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>参数  
 `E`  
 指针类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|构造函数。|  
  
## <a name="remarks"></a>备注  
 此类提供的构造函数和派生方法从[CAtlArray](../../atl/reference/catlarray-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)以帮助存储智能指针集合类对象的创建。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CAtlArray`  
  
 `CAutoPtrArray`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcoll.h  
  
##  <a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray  
 构造函数。  
  
```
CAutoPtrArray() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化智能指针数组。  
  
## <a name="see-also"></a>请参阅  
 [CAtlArray 类](../../atl/reference/catlarray-class.md)   
 [CAutoPtrElementTraits 类](../../atl/reference/cautoptrelementtraits-class.md)   
 [CAutoPtrList 类](../../atl/reference/cautoptrlist-class.md)   
 [类概述](../../atl/atl-class-overview.md)

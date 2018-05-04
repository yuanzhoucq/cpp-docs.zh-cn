---
title: CAutoPtrList 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9101d66de6782d1a060a8acdfb0d02e9971bb9c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 类
构造的智能指针的列表时，此类提供有用的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>参数  
 `E`  
 指针类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|构造函数。|  
  
## <a name="remarks"></a>备注  
 此类提供的构造函数和派生方法从[CAtlList](../../atl/reference/catllist-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)以帮助创建存储智能指针列表对象。 类[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)数组对象中提供的类似函数。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList  
 构造函数。  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 块的大小，默认值为 10。  
  
### <a name="remarks"></a>备注  
 块大小是内存的分配需要一个新的元素时量的度量值。 更大的块大小减少到内存分配例程的调用，但使用更多资源。  
  
## <a name="see-also"></a>请参阅  
 [CAtlList 类](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits 类](../../atl/reference/cautoptrelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)

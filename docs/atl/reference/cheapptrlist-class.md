---
title: "CHeapPtrList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs: C++
helpviewer_keywords: CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 18d4847c53e7926abecba43dd55f44acd22ed2f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cheapptrlist-class"></a>CHeapPtrList 类
构造的堆指针的列表时，此类提供有用的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>参数  
 `E`  
 要存储在集合类的对象类型。  
  
 `Allocator`  
 要使用的内存分配类。 默认值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|构造函数。|  
  
## <a name="remarks"></a>备注  
 此类提供的构造函数和派生方法从[CAtlList](../../atl/reference/catllist-class.md)和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)以帮助存储堆指针集合类对象的创建。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList  
 构造函数。  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBlockSize`  
 块大小。  
  
### <a name="remarks"></a>备注  
 块大小是内存的分配需要一个新的元素时量的度量值。 更大的块大小减少到内存分配例程的调用，但使用更多资源。  
  
## <a name="see-also"></a>另请参阅  
 [CAtlList 类](../../atl/reference/catllist-class.md)   
 [CHeapPtr 类](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits 类](../../atl/reference/cheapptrelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)

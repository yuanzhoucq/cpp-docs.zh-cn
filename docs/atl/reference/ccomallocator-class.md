---
title: "CComAllocator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 370a52e87bcbb4849883ea03016cc462030ad028
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomallocator-class"></a>CComAllocator 类
此类提供用于管理使用 COM 内存例程的内存的方法。  
  
## <a name="syntax"></a>语法  
  
```
class CComAllocator
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|调用此静态方法，以分配内存。|  
|[CComAllocator::Free](#free)|调用此静态方法以释放分配的内存。|  
|[CComAllocator::Reallocate](#reallocate)|调用此静态方法，以重新分配内存。|  
  
## <a name="remarks"></a>备注  
 此类由[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)提供 COM 内存分配例程。 对应项类中， [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)，提供使用 CRT 例程的相同方法。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlbase.h  
  
##  <a name="allocate"></a>CComAllocator::Allocate  
 调用此静态函数以分配内存。  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 要分配的字节数。  
  
### <a name="return-value"></a>返回值  
 返回指向已分配空间的 void 指针；如果可用内存不足，则返回 NULL。  
  
### <a name="remarks"></a>备注  
 分配内存。 请参阅[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)有关详细信息。  
  
##  <a name="free"></a>CComAllocator::Free  
 调用此静态函数以释放分配的内存。  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向已分配内存的指针。  
  
### <a name="remarks"></a>备注  
 释放分配的内存。 请参阅[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)有关详细信息。  
  
##  <a name="reallocate"></a>CComAllocator::Reallocate  
 调用此静态函数以重新分配内存。  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向已分配内存的指针。  
  
 `nBytes`  
 要重新分配的字节数。  
  
### <a name="return-value"></a>返回值  
 如果没有足够的内存分配的空间，或者为 NULL 返回 void 的指针  
  
### <a name="remarks"></a>备注  
 调整已分配内存的大小。 请参阅[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)   
 [CCRTAllocator 类](../../atl/reference/ccrtallocator-class.md)   
 [类概述](../../atl/atl-class-overview.md)

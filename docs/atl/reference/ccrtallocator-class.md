---
title: "CCRTAllocator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84c8f800e0b68e23fe33ca0a7e1c1d977bcc344e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccrtallocator-class"></a>CCRTAllocator 类
此类提供用于管理使用 CRT 内存例程的内存的方法。  
  
## <a name="syntax"></a>语法  
  
```
class ATL::CCRTAllocator
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Ccrtallocator:: Allocate](#allocate)|（静态）调用此方法以分配内存。|  
|[Ccrtallocator:: Free](#free)|（静态）调用此方法以释放内存。|  
|[Ccrtallocator:: Reallocate](#reallocate)|（静态）调用此方法以重新分配内存。|  
  
## <a name="remarks"></a>备注  
 此类由[CHeapPtr](../../atl/reference/cheapptr-class.md)提供 CRT 内存分配例程。 对应项类中， [CComAllocator](../../atl/reference/ccomallocator-class.md)，提供了使用 COM 例程的相同方法。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcore.h  
  
##  <a name="allocate"></a>Ccrtallocator:: Allocate  
 调用此静态函数以分配内存。  
  
```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 要分配的字节数。  
  
### <a name="return-value"></a>返回值  
 返回指向已分配空间的 void 指针；如果可用内存不足，则返回 NULL。  
  
### <a name="remarks"></a>备注  
 分配内存。 请参阅[malloc](../../c-runtime-library/reference/malloc.md)有关详细信息。  
  
##  <a name="free"></a>Ccrtallocator:: Free  
 调用此静态函数以释放内存。  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向已分配内存的指针。  
  
### <a name="remarks"></a>备注  
 释放分配的内存。 请参阅[免费](../../c-runtime-library/reference/free.md)有关详细信息。  
  
##  <a name="reallocate"></a>Ccrtallocator:: Reallocate  
 调用此静态函数以重新分配内存。  
  
```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向已分配内存的指针。  
  
 `nBytes`  
 要重新分配的字节数。  
  
### <a name="return-value"></a>返回值  
 如果没有足够的内存，请返回指向已分配空间的 void 指针，或返回 NULL。  
  
### <a name="remarks"></a>备注  
 调整已分配内存的大小。 请参阅[realloc](../../c-runtime-library/reference/realloc.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [CHeapPtr 类](../../atl/reference/cheapptr-class.md)   
 [CComAllocator 类](../../atl/reference/ccomallocator-class.md)   
 [类概述](../../atl/atl-class-overview.md)

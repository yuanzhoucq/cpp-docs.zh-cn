---
title: "CCRTHeap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
caps.latest.revision: 19
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1b4df6949794981867051437835d043196613afa
ms.lasthandoff: 02/24/2017

---
# <a name="ccrtheap-class"></a>CCRTHeap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 CRT 堆函数。  
  
## <a name="syntax"></a>语法  
  
```
class CCRTHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Ccrtheap:: Allocate](#allocate)|调用此方法来分配内存块。|  
|[Ccrtheap:: Free](#free)|调用此方法释放此内存管理器分配的内存块。|  
|[CCRTHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块的分配的大小。|  
|[CCRTHeap::Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|  
  
## <a name="remarks"></a>备注  
 `CCRTHeap`实现内存分配函数使用的 CRT 堆函数，其中包括[malloc](../../c-runtime-library/reference/malloc.md)，[免费](../../c-runtime-library/reference/free.md)， [realloc](../../c-runtime-library/reference/realloc.md)，和[_msize](../../c-runtime-library/reference/msize.md)。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlmem.h  
  
##  <a name="allocate"></a>Ccrtheap:: Allocate  
 调用此方法来分配内存块。  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 新内存块中请求的字节数。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配内存块的起始位置。  
  
### <a name="remarks"></a>备注  
 调用[ccrtheap:: Free](#free)或[CCRTHeap::Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[malloc](../../c-runtime-library/reference/malloc.md)。  
  
##  <a name="free"></a>Ccrtheap:: Free  
 调用此方法释放此内存管理器分配的内存块。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。  
  
### <a name="remarks"></a>备注  
 使用实现[免费](../../c-runtime-library/reference/free.md)。  
  
##  <a name="getsize"></a>CCRTHeap::GetSize  
 调用此方法以获取此内存管理器分配的内存块的分配的大小。  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。  
  
### <a name="return-value"></a>返回值  
 以字节为单位返回分配的内存块的大小。  
  
### <a name="remarks"></a>备注  
 使用实现[_msize](../../c-runtime-library/reference/msize.md)。  
  
##  <a name="reallocate"></a>CCRTHeap::Reallocate  
 调用此方法以重新分配由该内存管理器分配的内存。  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。  
  
 `nBytes`  
 新内存块中请求的字节数。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配内存块的起始位置。  
  
### <a name="remarks"></a>备注  
 调用[ccrtheap:: Free](#free)来释放由此方法分配的内存。 使用实现[realloc](../../c-runtime-library/reference/realloc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CComHeap 类](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap 类](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)


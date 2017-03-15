---
title: "CLocalHeap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CLocalHeap
- ATL::CLocalHeap
- CLocalHeap
dev_langs:
- C++
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 6a5caaa360970578aee4432fd40af9aa0e391d90
ms.lasthandoff: 02/24/2017

---
# <a name="clocalheap-class"></a>CLocalHeap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 本地堆函数。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CLocalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CLocalHeap::Allocate](#allocate)|调用此方法来分配内存块。|  
|[CLocalHeap::Free](#free)|调用此方法释放此内存管理器分配的内存块。|  
|[CLocalHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块的分配的大小。|  
|[CLocalHeap::Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|  
  
## <a name="remarks"></a>备注  
 `CLocalHeap`实现内存分配函数使用 Win32 本地堆函数。  
  
> [!NOTE]
>  本地堆函数慢于其他内存管理函数，并且不提供尽可能多的功能。 因此，新的应用程序应使用[堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 这些是位于[CWin32Heap](../../atl/reference/cwin32heap-class.md)类。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlmem.h  
  
##  <a name="a-nameallocatea--clocalheapallocate"></a><a name="allocate"></a>CLocalHeap::Allocate  
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
 调用[CLocalHeap::Free](#free)或[CLocalHeap::Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)标志参数的**LMEM_FIXED**。  
  
##  <a name="a-namefreea--clocalheapfree"></a><a name="free"></a>CLocalHeap::Free  
 调用此方法释放此内存管理器分配的内存块。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。  
  
### <a name="remarks"></a>备注  
 使用实现[LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)。  
  
##  <a name="a-namegetsizea--clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap::GetSize  
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
 使用实现[LocalSize](http://msdn.microsoft.com/library/windows/desktop/aa366745)。  
  
##  <a name="a-namereallocatea--clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap::Reallocate  
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
 调用[CLocalHeap::Free](#free)来释放由此方法分配的内存。  
  
 使用实现[LocalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CComHeap 类](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 类](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)


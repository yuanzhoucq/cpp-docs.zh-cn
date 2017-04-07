---
title: "CGlobalHeap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
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
ms.openlocfilehash: f8b4276202a507e2afeb05d10a37fa16565870e8
ms.lasthandoff: 02/24/2017

---
# <a name="cglobalheap-class"></a>CGlobalHeap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 全局堆函数。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CGlobalHeap::Allocate](#allocate)|调用此方法来分配内存块。|  
|[CGlobalHeap::Free](#free)|调用此方法释放此内存管理器分配的内存块。|  
|[CGlobalHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块的分配的大小。|  
|[CGlobalHeap::Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|  
  
## <a name="remarks"></a>备注  
 `CGlobalHeap`实现内存分配函数使用 Win32 全局堆函数。  
  
> [!NOTE]
>  全局堆函数慢于其他内存管理函数，并且不提供尽可能多的功能。 因此，新的应用程序应使用[堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 这些是位于[CWin32Heap](../../atl/reference/cwin32heap-class.md)类。 DDE 和剪贴板函数仍使用全局函数。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlmem.h  
  
##  <a name="allocate"></a>CGlobalHeap::Allocate  
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
 调用[CGlobalHeap::Free](#free)或[CGlobalHeap::Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)标志参数的**GMEM_FIXED**。  
  
##  <a name="free"></a>CGlobalHeap::Free  
 调用此方法释放此内存管理器分配的内存块。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。  
  
### <a name="remarks"></a>备注  
 使用实现[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)。  
  
##  <a name="getsize"></a>CGlobalHeap::GetSize  
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
 使用实现[GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593)。  
  
##  <a name="reallocate"></a>CGlobalHeap::Reallocate  
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
 调用[CGlobalHeap::Free](#free)来释放由此方法分配的内存。  
  
 使用实现[以及](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CComHeap 类](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap 类](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap 类](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)


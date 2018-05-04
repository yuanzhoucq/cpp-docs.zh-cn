---
title: CLocalHeap 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 299c672d65d7568539473dfc284833c2583a2220
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="clocalheap-class"></a>CLocalHeap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 本地堆函数。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CLocalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Clocalheap:: Allocate](#allocate)|调用此方法来分配内存块。|  
|[Clocalheap:: Free](#free)|调用此方法以释放此内存管理器分配的内存块。|  
|[CLocalHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块分配的大小。|  
|[Clocalheap:: Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|  
  
## <a name="remarks"></a>备注  
 `CLocalHeap` 实现使用 Win32 本地堆函数的内存分配函数。  
  
> [!NOTE]
>  本地堆函数慢于其他内存管理函数，并且未提供尽可能多的功能。 因此，新的应用程序应使用[堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 这些是位于[CWin32Heap](../../atl/reference/cwin32heap-class.md)类。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## <a name="requirements"></a>要求  
 **标头：** atlmem.h  
  
##  <a name="allocate"></a>  Clocalheap:: Allocate  
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
 调用[clocalheap:: Free](#free)或[clocalheap:: Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723)标志参数的**LMEM_FIXED**。  
  
##  <a name="free"></a>  Clocalheap:: Free  
 调用此方法以释放此内存管理器分配的内存块。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。 NULL 是一个有效的值，不执行任何操作。  
  
### <a name="remarks"></a>备注  
 使用实现[LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730)。  
  
##  <a name="getsize"></a>  CLocalHeap::GetSize  
 调用此方法以获取此内存管理器分配的内存块分配的大小。  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。  
  
### <a name="return-value"></a>返回值  
 返回以字节为单位分配的内存块的大小。  
  
### <a name="remarks"></a>备注  
 使用实现[LocalSize](http://msdn.microsoft.com/library/windows/desktop/aa366745)。  
  
##  <a name="reallocate"></a>  Clocalheap:: Reallocate  
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
 调用[clocalheap:: Free](#free)来释放由此方法分配的内存。  
  
 使用实现[LocalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CComHeap 类](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 类](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

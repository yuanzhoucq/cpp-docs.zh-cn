---
title: CGlobalHeap 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bef811807c90507184690d1a29d4debd00cc6fda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363329"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 全局堆函数。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cglobalheap:: Allocate](#allocate)|调用此方法来分配内存块。|  
|[Cglobalheap:: Free](#free)|调用此方法以释放此内存管理器分配的内存块。|  
|[CGlobalHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块分配的大小。|  
|[Cglobalheap:: Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|  
  
## <a name="remarks"></a>备注  
 `CGlobalHeap` 实现使用 Win32 全局堆函数的内存分配函数。  
  
> [!NOTE]
>  全局堆函数慢于其他内存管理函数，并且未提供尽可能多的功能。 因此，新的应用程序应使用[堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 这些是位于[CWin32Heap](../../atl/reference/cwin32heap-class.md)类。 DDE 和剪贴板函数仍使用全局函数。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>要求  
 **标头：** atlmem.h  
  
##  <a name="allocate"></a>  Cglobalheap:: Allocate  
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
 调用[cglobalheap:: Free](#free)或[cglobalheap:: Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)标志参数的**GMEM_FIXED**。  
  
##  <a name="free"></a>  Cglobalheap:: Free  
 调用此方法以释放此内存管理器分配的内存块。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。 NULL 是一个有效的值，不执行任何操作。  
  
### <a name="remarks"></a>备注  
 使用实现[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)。  
  
##  <a name="getsize"></a>  CGlobalHeap::GetSize  
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
 使用实现[GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593)。  
  
##  <a name="reallocate"></a>  Cglobalheap:: Reallocate  
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
 调用[cglobalheap:: Free](#free)来释放由此方法分配的内存。  
  
 使用实现[GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CComHeap 类](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap 类](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap 类](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

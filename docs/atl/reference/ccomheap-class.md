---
title: "CComHeap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
caps.latest.revision: 22
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
ms.openlocfilehash: 323ad1aed4bae706ecbf66de769e33873f20c149
ms.lasthandoff: 02/24/2017

---
# <a name="ccomheap-class"></a>CComHeap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 COM 内存分配函数。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CComHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CComHeap::Allocate](#allocate)|调用此方法来分配内存块。|  
|[Ccomheap:: Free](#free)|调用此方法释放此内存管理器分配的内存块。|  
|[CComHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块的分配的大小。|  
|[Ccomheap:: Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|  
  
## <a name="remarks"></a>备注  
 `CComHeap`实现内存分配函数使用 COM 分配函数，其中包括[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)， [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)， [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)，和[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)。 最大可分配的内存量等于**INT_MAX** (2147483647) 字节。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## <a name="requirements"></a>要求  
 **标头︰** ATLComMem.h  
  
##  <a name="allocate"></a>CComHeap::Allocate  
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
 调用[ccomheap:: Free](#free)或[ccomheap:: Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)。  
  
##  <a name="free"></a>Ccomheap:: Free  
 调用此方法释放此内存管理器分配的内存块。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。  
  
### <a name="remarks"></a>备注  
 使用实现[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)。  
  
##  <a name="getsize"></a>CComHeap::GetSize  
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
 使用实现[IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)。  
  
##  <a name="reallocate"></a>Ccomheap:: Reallocate  
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
 调用[ccomheap:: Free](#free)来释放由此方法分配的内存。  
  
 使用实现[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)。  
  
## <a name="see-also"></a>另请参阅  
 [DynamicConsumer 示例](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap 类](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 类](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)


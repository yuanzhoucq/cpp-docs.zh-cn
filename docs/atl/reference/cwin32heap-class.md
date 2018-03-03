---
title: "CWin32Heap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
dev_langs:
- C++
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67856242c63639101185eb6f6dcfd4902f0ef48c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cwin32heap-class"></a>CWin32Heap 类
此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 堆分配函数。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CWin32Heap : public IAtlMemMgr
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWin32Heap::CWin32Heap](#cwin32heap)|构造函数。|  
|[CWin32Heap:: ~ CWin32Heap](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cwin32heap:: Allocate](#allocate)|从堆对象中分配内存块。|  
|[Cwin32heap:: Attach](#attach)|将堆对象附加到现有堆中。|  
|[CWin32Heap::Detach](#detach)|将现有堆中的堆对象分离。|  
|[Cwin32heap:: Free](#free)|将释放以前从堆分配的内存。|  
|[CWin32Heap::GetSize](#getsize)|返回从堆对象分配的内存块的大小。|  
|[Cwin32heap:: Reallocate](#reallocate)|从堆对象中重新分配内存块。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|一个标志，用于确定当前的所有权的堆句柄。|  
|[CWin32Heap::m_hHeap](#m_hheap)|堆对象句柄。|  
  
## <a name="remarks"></a>备注  
 `CWin32Heap`实现使用 Win32 堆分配函数，包括内存分配方法[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)和[HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)。 其他堆与类不同，`CWin32Heap`需要分配内存之前，请提供有效的堆句柄： 其他类默认为使用进程堆。 可以提供句柄，到构造函数或[cwin32heap:: Attach](#attach)方法。 请参阅[CWin32Heap::CWin32Heap](#cwin32heap)更多详细信息的方法。  
  
## <a name="example"></a>示例  
 请参阅示例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlmem.h  
  
##  <a name="allocate"></a>Cwin32heap:: Allocate  
 从堆对象中分配内存块。  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `nBytes`  
 新内存块中请求的字节数。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配的内存块。  
  
### <a name="remarks"></a>备注  
 调用[cwin32heap:: Free](#free)或[cwin32heap:: Reallocate](#reallocate)来释放由此方法分配的内存。  
  
 使用实现[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)。  
  
##  <a name="attach"></a>Cwin32heap:: Attach  
 将堆对象附加到现有堆中。  
  
```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```  
  
### <a name="parameters"></a>参数  
 `hHeap`  
 现有堆句柄。  
  
 `bTakeOwnership`  
 标志指示如果`CWin32Heap`对象是接管堆的资源的所有权。  
  
### <a name="remarks"></a>备注  
 如果`bTakeOwnership`为 TRUE，`CWin32Heap`对象负责删除堆句柄。  
  
##  <a name="cwin32heap"></a>CWin32Heap::CWin32Heap  
 构造函数。  
  
```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```  
  
### <a name="parameters"></a>参数  
 `hHeap`  
 一个现有的堆对象。  
  
 `dwFlags`  
 在创建堆时使用的标志。  
  
 *nInitialSize*  
 堆的初始大小。  
  
 `nMaxSize`  
 堆的最大大小。  
  
### <a name="remarks"></a>备注  
 在分配内存之前，必须为 `CWin32Heap` 对象提供有效的堆句柄。 实现此目的的最简单的方法是使用进程堆：  
  
 [!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]  
  
 也可以向构造函数提供现有堆句柄，在这种情况下，新对象不会接管此堆的所有权。 在删除 `CWin32Heap` 对象时，原始堆句柄仍将有效。  
  
 现有堆还附加到新对象、 使用[cwin32heap:: Attach](#attach)。  
  
 如果在单个线程中执行所有操作时需要堆，则最佳方法是创建如下对象：  
  
 [!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]  
  
 参数**HEAP_NO_SERIALIZE**指定堆函数分配和释放内存，随着性能的相应增加时，将不使用互相排斥。  
  
 第三个参数默认为 0，这使堆能够根据需要增长。 请参阅[HeapCreate](http://msdn.microsoft.com/library/windows/desktop/aa366599\(v=vs.85\).aspx)有关内存大小和标志的说明。  
  
##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap  
 析构函数。  
  
```
~CWin32Heap() throw();
```  
  
### <a name="remarks"></a>备注  
 销毁堆句柄，如果`CWin32Heap`对象具有此堆的所有权。  
  
##  <a name="detach"></a>CWin32Heap::Detach  
 将现有堆中的堆对象分离。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回到的对象以前已附加堆的句柄。  
  
##  <a name="free"></a>Cwin32heap:: Free  
 释放以前从由堆分配的内存[cwin32heap:: Allocate](#allocate)或[cwin32heap:: Reallocate](#reallocate)。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向要释放的内存块指针。 NULL 是一个有效的值，不执行任何操作。  
  
##  <a name="getsize"></a>CWin32Heap::GetSize  
 返回从堆对象分配的内存块的大小。  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 该方法将获取其大小的内存块的指针。 这是通过返回的指针[cwin32heap:: Allocate](#allocate)或[cwin32heap:: Reallocate](#reallocate)。  
  
### <a name="return-value"></a>返回值  
 返回的大小，以字节为单位分配的内存块。  
  
##  <a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap  
 用于确定当前的所有权，堆句柄存储在一个标志[m_hHeap](#m_hheap)。  
  
```
bool m_bOwnHeap;
```  
  
##  <a name="m_hheap"></a>CWin32Heap::m_hHeap  
 堆对象句柄。  
  
```
HANDLE m_hHeap;
```  
  
### <a name="remarks"></a>备注  
 一个用于存储堆对象的句柄的变量。  
  
##  <a name="reallocate"></a>Cwin32heap:: Reallocate  
 从堆对象中重新分配内存块。  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向要重新分配的内存块的指针。  
  
 `nBytes`  
 已分配块的新大小（以字节为单位）。 块可放大或缩小。  
  
### <a name="return-value"></a>返回值  
 将指针返回到新分配的内存块。  
  
### <a name="remarks"></a>备注  
 如果`p`为 NULL，则假定尚未分配内存块和[cwin32heap:: Allocate](#allocate)使用的自变量调用`nBytes`。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)   
 [CLocalHeap 类](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 类](../../atl/reference/ccrtheap-class.md)   
 [CComHeap 类](../../atl/reference/ccomheap-class.md)

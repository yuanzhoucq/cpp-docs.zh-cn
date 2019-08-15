---
title: CGlobalHeap 类
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: 2b5aa09357ddcc77b6b10de58545bea86eff2488
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496761"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 类

此类使用 Win32 全局堆函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CGlobalHeap::Allocate](#allocate)|调用此方法来分配内存块。|
|[CGlobalHeap::Free](#free)|调用此方法可释放此内存管理器分配的内存块。|
|[CGlobalHeap::GetSize](#getsize)|调用此方法可获取此内存管理器分配的内存块的分配大小。|
|[CGlobalHeap::Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CGlobalHeap`使用 Win32 全局堆函数实现内存分配函数。

> [!NOTE]
>  全局堆函数比其他内存管理函数慢, 并且不提供任何多个功能。 因此, 新应用程序应使用[堆函数](/windows/win32/Memory/heap-functions)。 这些都在[CWin32Heap](../../atl/reference/cwin32heap-class.md)类中提供。 全局函数仍用于 DDE 和剪贴板函数。

## <a name="example"></a>示例

请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>要求

**标头:** atlmem

##  <a name="allocate"></a>CGlobalHeap:: Allocate

调用此方法来分配内存块。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*nBytes*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[CGlobalHeap:: Free](#free)或[CGlobalHeap:: 重新分配](#reallocate)以释放此方法分配的内存。

使用[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)和 GMEM_FIXED 参数实现。

##  <a name="free"></a>CGlobalHeap:: Free

调用此方法可释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向此内存管理器以前分配的内存的指针。 NULL 是有效的值并且不执行任何操作。

### <a name="remarks"></a>备注

使用[GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)实现。

##  <a name="getsize"></a>CGlobalHeap:: GetSize

调用此方法可获取此内存管理器分配的内存块的分配大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向此内存管理器以前分配的内存的指针。

### <a name="return-value"></a>返回值

返回分配的内存块的大小 (以字节为单位)。

### <a name="remarks"></a>备注

使用[GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize)实现。

##  <a name="reallocate"></a>CGlobalHeap:: 重新分配

调用此方法以重新分配由该内存管理器分配的内存。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向此内存管理器以前分配的内存的指针。

*nBytes*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[CGlobalHeap:: free](#free)可释放由此方法分配的内存。

使用[GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)实现。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap 类](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap 类](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

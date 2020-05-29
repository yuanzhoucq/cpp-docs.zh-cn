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
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326944"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 类

此类使用 Win32 全局堆函数实现[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CGlobalHeap：分配](#allocate)|调用此方法来分配内存块。|
|[CGlobalHeap：免费](#free)|调用此方法以释放此内存管理器分配的内存块。|
|[CGlobalHeap：获取大小](#getsize)|调用此方法获取此内存管理器分配的内存块的分配大小。|
|[CGlobalHeap：重新分配](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CGlobalHeap`使用 Win32 全局堆函数实现内存分配函数。

> [!NOTE]
> 全局堆函数比其他内存管理函数慢，并且不提供尽可能多的功能。 因此，新应用程序应使用[堆函数](/windows/win32/Memory/heap-functions)。 这些在[CWin32Heap](../../atl/reference/cwin32heap-class.md)类中可用。 DDE 和剪贴板函数仍使用全局函数。

## <a name="example"></a>示例

请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>要求

**标题：** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap：分配

调用此方法来分配内存块。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*n 字节*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[CGlobalHeap：：免费](#free)或[CGlobalHeap：重新分配](#reallocate)以释放此方法分配的内存。

使用带有GMEM_FIXED标志参数的[Global Alloc](/windows/win32/api/winbase/nf-winbase-globalalloc)实现。

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap：免费

调用此方法以释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。

### <a name="remarks"></a>备注

使用[GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)实现 。

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap：获取大小

调用此方法获取此内存管理器分配的内存块的分配大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。

### <a name="return-value"></a>返回值

返回以字节为单位的分配内存块的大小。

### <a name="remarks"></a>备注

使用[全局大小](/windows/win32/api/winbase/nf-winbase-globalsize)实现 。

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap：重新分配

调用此方法以重新分配由该内存管理器分配的内存。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。

*n 字节*<br/>
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[CGlobalHeap：：可自由](#free)释放此方法分配的内存。

使用[GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)实现。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)<br/>
[C本地堆类](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap 类](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

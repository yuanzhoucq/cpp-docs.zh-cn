---
title: C本地堆类
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 303e3b85ad11c309f862f59d6ec610701c4ef6db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326763"
---
# <a name="clocalheap-class"></a>C本地堆类

此类使用 Win32 本地堆函数实现[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CLocalHeap：分配](#allocate)|调用此方法来分配内存块。|
|[CLocalHeap：免费](#free)|调用此方法以释放此内存管理器分配的内存块。|
|[CLocalHeap：获取大小](#getsize)|调用此方法获取此内存管理器分配的内存块的分配大小。|
|[CLocalHeap：重新分配](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CLocalHeap`使用 Win32 本地堆函数实现内存分配函数。

> [!NOTE]
> 本地堆函数比其他内存管理函数慢，并且不提供尽可能多的功能。 因此，新应用程序应使用[堆函数](/windows/win32/Memory/heap-functions)。 这些在[CWin32Heap](../../atl/reference/cwin32heap-class.md)类中可用。

## <a name="example"></a>示例

请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>要求

**标题：** atlmem.h

## <a name="clocalheapallocate"></a><a name="allocate"></a>CLocalHeap：分配

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

调用[CLocalHeap：：免费](#free)或[ClocalHeap：重新分配](#reallocate)以释放此方法分配的内存。

使用带有LMEM_FIXED标志参数的[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)实现。

## <a name="clocalheapfree"></a><a name="free"></a>CLocalHeap：免费

调用此方法以释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。

### <a name="remarks"></a>备注

使用[本地自由](/windows/win32/api/winbase/nf-winbase-localfree)实现 。

## <a name="clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap：获取大小

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

使用[本地大小](/windows/win32/api/winbase/nf-winbase-localsize)实现 。

## <a name="clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap：重新分配

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

调用[CLocalHeap：：可自由](#free)释放此方法分配的内存。

使用[本地ReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc)实现。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 类](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

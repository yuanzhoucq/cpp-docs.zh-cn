---
title: CLocalHeap 类
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
ms.openlocfilehash: 53288bea8a50f62437eab4dd81d5d816abf78f44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258827"
---
# <a name="clocalheap-class"></a>CLocalHeap 类

此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 本地堆函数。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|调用此方法来分配内存块。|
|[CLocalHeap::Free](#free)|调用此方法来释放此内存管理器分配的内存块。|
|[CLocalHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块的分配的大小。|
|[CLocalHeap::Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CLocalHeap` 实现使用 Win32 本地堆函数的内存分配函数。

> [!NOTE]
>  本地堆函数比其他内存管理函数，并不提供尽可能多的功能。 因此，应使用新的应用程序[堆函数](/windows/desktop/Memory/heap-functions)。 这些功能中位于[CWin32Heap](../../atl/reference/cwin32heap-class.md)类。

## <a name="example"></a>示例

有关示例，请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>要求

**标头：** atlmem.h

##  <a name="allocate"></a>  CLocalHeap::Allocate

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

调用[clocalheap:: Free](#free)或[clocalheap:: Reallocate](#reallocate)来释放由此方法分配的内存。

使用实现[LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) LMEM_FIXED 的标记参数。

##  <a name="free"></a>  Clocalheap:: Free

调用此方法来释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向此内存管理器以前分配的内存的指针。 NULL 是一个有效的值，不执行任何操作。

### <a name="remarks"></a>备注

使用实现[LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree)。

##  <a name="getsize"></a>  CLocalHeap::GetSize

调用此方法以获取此内存管理器分配的内存块的分配的大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向此内存管理器以前分配的内存的指针。

### <a name="return-value"></a>返回值

以字节为单位返回已分配的内存块的大小。

### <a name="remarks"></a>备注

使用实现[LocalSize](/windows/desktop/api/winbase/nf-winbase-localsize)。

##  <a name="reallocate"></a>  CLocalHeap::Reallocate

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

调用[clocalheap:: Free](#free)来释放由此方法分配的内存。

使用实现[LocalReAlloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 类](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

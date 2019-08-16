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
ms.openlocfilehash: a302ba4ea55c42ce214c8de4a24be843d6cb1b9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496745"
---
# <a name="clocalheap-class"></a>CLocalHeap 类

此类使用 Win32 本地堆函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|调用此方法来分配内存块。|
|[CLocalHeap::Free](#free)|调用此方法可释放此内存管理器分配的内存块。|
|[CLocalHeap::GetSize](#getsize)|调用此方法可获取此内存管理器分配的内存块的分配大小。|
|[CLocalHeap::Reallocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CLocalHeap`使用 Win32 本地堆函数实现内存分配函数。

> [!NOTE]
>  本地堆函数比其他内存管理函数慢, 并且不提供任何多个功能。 因此, 新应用程序应使用[堆函数](/windows/win32/Memory/heap-functions)。 这些都在[CWin32Heap](../../atl/reference/cwin32heap-class.md)类中提供。

## <a name="example"></a>示例

请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>要求

**标头:** atlmem

##  <a name="allocate"></a>CLocalHeap:: Allocate

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

调用[CLocalHeap:: Free](#free)或[CLocalHeap:: 重新分配](#reallocate)以释放此方法分配的内存。

使用[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)和 LMEM_FIXED 参数实现。

##  <a name="free"></a>CLocalHeap:: Free

调用此方法可释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向此内存管理器以前分配的内存的指针。 NULL 是有效的值并且不执行任何操作。

### <a name="remarks"></a>备注

使用[LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)实现。

##  <a name="getsize"></a>CLocalHeap:: GetSize

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

使用[LocalSize](/windows/win32/api/winbase/nf-winbase-localsize)实现。

##  <a name="reallocate"></a>CLocalHeap:: 重新分配

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

调用[CLocalHeap:: free](#free)可释放由此方法分配的内存。

使用[LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc)实现。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 类](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

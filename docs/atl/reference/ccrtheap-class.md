---
title: CCRTHeap 类
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327165"
---
# <a name="ccrtheap-class"></a>CCRTHeap 类

此类使用 CRT 堆函数实现[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

## <a name="syntax"></a>语法

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCRTHeap：分配](#allocate)|调用此方法来分配内存块。|
|[CCRTHeap：免费](#free)|调用此方法以释放此内存管理器分配的内存块。|
|[CCRTHeap：获取大小](#getsize)|调用此方法获取此内存管理器分配的内存块的分配大小。|
|[CCRTHeap：重新分配](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CCRTHeap`使用 CRT 堆函数实现内存分配函数，包括[malloc、](../../c-runtime-library/reference/malloc.md)[自由](../../c-runtime-library/reference/free.md)、[真实](../../c-runtime-library/reference/realloc.md)和[_msize。](../../c-runtime-library/reference/msize.md)

## <a name="example"></a>示例

请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的示例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>要求

**标题：** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeap：分配

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

调用[CCRTHeap：：免费](#free)或[CCRTHeap：重新分配](#reallocate)以释放此方法分配的内存。

使用[malloc](../../c-runtime-library/reference/malloc.md)实现。

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeap：免费

调用此方法以释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向此内存管理器以前分配的内存的指针。 NULL 是有效的值，不执行任何操作。

### <a name="remarks"></a>备注

使用[免费](../../c-runtime-library/reference/free.md)实现。

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeap：获取大小

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

使用[_msize](../../c-runtime-library/reference/msize.md)实现。

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeap：重新分配

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

调用[CCRTHeap：：免费](#free)释放此方法分配的内存。 使用[realloc](../../c-runtime-library/reference/realloc.md)实现。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComHeap 类](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)<br/>
[C本地堆类](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

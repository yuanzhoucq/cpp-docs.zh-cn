---
title: CComAllocator 类
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321141"
---
# <a name="ccomallocator-class"></a>CComAllocator 类

此类提供了使用 COM 内存例程管理内存的方法。

## <a name="syntax"></a>语法

```
class CComAllocator
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComallocator：：分配](#allocate)|调用此静态方法以分配内存。|
|[CComallocator：免费](#free)|调用此静态方法以释放分配的内存。|
|[CComallocator：：重新分配](#reallocate)|调用此静态方法重新分配内存。|

## <a name="remarks"></a>备注

[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)使用此类来提供 COM 内存分配例程。 对应类[CCRT分配器](../../atl/reference/ccrtallocator-class.md)使用 CRT 例程提供相同的方法。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComallocator：：分配

调用此静态函数以分配内存。

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*n 字节*<br/>
要分配的字节数。

### <a name="return-value"></a>返回值

返回指向已分配空间的 void 指针；如果可用内存不足，则返回 NULL。

### <a name="remarks"></a>备注

分配内存。 有关详细信息[，请参阅 CoTaskMemAlloc。](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)

## <a name="ccomallocatorfree"></a><a name="free"></a>CComallocator：免费

调用此静态函数以释放分配的内存。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向已分配内存的指针。

### <a name="remarks"></a>备注

释放分配的内存。 有关详细信息，请参阅[CoTaskMem 免费](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)。

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComallocator：：重新分配

调用此静态函数以重新分配内存。

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向已分配内存的指针。

*n 字节*<br/>
要重新分配的字节数。

### <a name="return-value"></a>返回值

返回指向已分配空间的空指针，如果内存不足，则返回 NULL

### <a name="remarks"></a>备注

调整已分配内存的大小。 有关详细信息[，请参阅 CoTaskMemRealloc。](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

## <a name="see-also"></a>另请参阅

[CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator 类](../../atl/reference/ccrtallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)

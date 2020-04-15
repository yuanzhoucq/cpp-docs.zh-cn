---
title: CCRTAllocator 类
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327170"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator 类

此类提供了使用 CRT 内存例程管理内存的方法。

## <a name="syntax"></a>语法

```
class ATL::CCRTAllocator
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCRTAllocator：：分配](#allocate)|（静态）调用此方法以分配内存。|
|[CCRTAllocator：免费](#free)|（静态）调用此方法以释放内存。|
|[CCRTAllocator：：重新分配](#reallocate)|（静态）调用此方法重新分配内存。|

## <a name="remarks"></a>备注

[CHeapPtr](../../atl/reference/cheapptr-class.md)使用此类来提供 CRT 内存分配例程。 对应类[CComAllocator](../../atl/reference/ccomallocator-class.md)提供了使用 COM 例程的相同方法。

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator：：分配

调用此静态函数以分配内存。

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*n 字节*<br/>
要分配的字节数。

### <a name="return-value"></a>返回值

返回指向已分配空间的 void 指针；如果可用内存不足，则返回 NULL。

### <a name="remarks"></a>备注

分配内存。 有关详细信息，请参阅[malloc。](../../c-runtime-library/reference/malloc.md)

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator：免费

调用此静态函数以释放内存。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向已分配内存的指针。

### <a name="remarks"></a>备注

释放分配的内存。 有关详细信息，请参阅[免费](../../c-runtime-library/reference/free.md)。

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator：：重新分配

调用此静态函数以重新分配内存。

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
指向已分配内存的指针。

*n 字节*<br/>
要重新分配的字节数。

### <a name="return-value"></a>返回值

如果没有足够的内存，请返回指向已分配空间的 void 指针，或返回 NULL。

### <a name="remarks"></a>备注

调整已分配内存的大小。 有关详细信息，请参阅[realloc。](../../c-runtime-library/reference/realloc.md)

## <a name="see-also"></a>另请参阅

[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator 类](../../atl/reference/ccomallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)

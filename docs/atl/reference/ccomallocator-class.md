---
title: CComAllocator 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f867d3a7ca81d190ee363c7539e56a62004eb377
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088938"
---
# <a name="ccomallocator-class"></a>CComAllocator 类

此类提供用于管理内存使用 COM 内存例程的方法。

## <a name="syntax"></a>语法

```
class CComAllocator
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|调用此静态方法分配内存。|
|[CComAllocator::Free](#free)|调用此静态方法来释放已分配的内存。|
|[CComAllocator::Reallocate](#reallocate)|调用此静态方法来重新分配内存。|

## <a name="remarks"></a>备注

使用此类[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)提供 COM 内存分配例程。 与类[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)，提供了使用 CRT 例程的相同方法。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="allocate"></a>  CComAllocator::Allocate

调用此静态函数以分配内存。

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*nBytes*<br/>
要分配的字节数。

### <a name="return-value"></a>返回值

返回指向已分配空间的 void 指针；如果可用内存不足，则返回 NULL。

### <a name="remarks"></a>备注

分配内存。 请参阅[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)的更多详细信息。

##  <a name="free"></a>  CComAllocator::Free

调用此静态函数以释放已分配的内存。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向已分配内存的指针。

### <a name="remarks"></a>备注

释放已分配的内存。 请参阅[CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree)的更多详细信息。

##  <a name="reallocate"></a>  CComAllocator::Reallocate

调用此静态函数以重新分配内存。

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
指向已分配内存的指针。

*nBytes*<br/>
要重新分配的字节数。

### <a name="return-value"></a>返回值

如果没有足够的内存分配的空间，或者为 NULL 返回 void 指针

### <a name="remarks"></a>备注

调整已分配内存的大小。 请参阅[CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)的更多详细信息。

## <a name="see-also"></a>请参阅

[CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator 类](../../atl/reference/ccrtallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)

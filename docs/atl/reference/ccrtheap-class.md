---
title: CCRTHeap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5244990d720cd36e0a040e9243067e49716d2549
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754756"
---
# <a name="ccrtheap-class"></a>CCRTHeap 类

此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 CRT 堆函数。

## <a name="syntax"></a>语法

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Ccrtheap:: Allocate](#allocate)|调用此方法来分配内存块。|
|[Ccrtheap:: Free](#free)|调用此方法来释放此内存管理器分配的内存块。|
|[CCRTHeap::GetSize](#getsize)|调用此方法以获取此内存管理器分配的内存块的分配的大小。|
|[Ccrtheap:: Allocate](#reallocate)|调用此方法以重新分配由该内存管理器分配的内存。|

## <a name="remarks"></a>备注

`CCRTHeap` 实现内存分配函数使用 CRT 堆函数，包括[malloc](../../c-runtime-library/reference/malloc.md)，[免费](../../c-runtime-library/reference/free.md)， [realloc](../../c-runtime-library/reference/realloc.md)，以及[_msize](../../c-runtime-library/reference/msize.md)。

## <a name="example"></a>示例

有关示例，请参阅[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>要求

**标头：** atlmem.h

##  <a name="allocate"></a>  Ccrtheap:: Allocate

调用此方法来分配内存块。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*nBytes*  
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[ccrtheap:: Free](#free)或[ccrtheap:: Reallocate](#reallocate)来释放由此方法分配的内存。

使用实现[malloc](../../c-runtime-library/reference/malloc.md)。

##  <a name="free"></a>  Ccrtheap:: Free

调用此方法来释放此内存管理器分配的内存块。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>参数

*p*  
指向此内存管理器以前分配的内存的指针。 NULL 是一个有效的值，不执行任何操作。

### <a name="remarks"></a>备注

使用实现[免费](../../c-runtime-library/reference/free.md)。

##  <a name="getsize"></a>  CCRTHeap::GetSize

调用此方法以获取此内存管理器分配的内存块的分配的大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>参数

*p*  
指向此内存管理器以前分配的内存的指针。

### <a name="return-value"></a>返回值

以字节为单位返回已分配的内存块的大小。

### <a name="remarks"></a>备注

使用实现[_msize](../../c-runtime-library/reference/msize.md)。

##  <a name="reallocate"></a>  Ccrtheap:: Allocate

调用此方法以重新分配由该内存管理器分配的内存。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*p*  
指向此内存管理器以前分配的内存的指针。

*nBytes*  
新内存块中请求的字节数。

### <a name="return-value"></a>返回值

将指针返回到新分配内存块的起始位置。

### <a name="remarks"></a>备注

调用[ccrtheap:: Free](#free)来释放由此方法分配的内存。 使用实现[realloc](../../c-runtime-library/reference/realloc.md)。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)   
[CComHeap 类](../../atl/reference/ccomheap-class.md)   
[CWin32Heap 类](../../atl/reference/cwin32heap-class.md)   
[CLocalHeap 类](../../atl/reference/clocalheap-class.md)   
[CGlobalHeap 类](../../atl/reference/cglobalheap-class.md)   
[IAtlMemMgr 类](../../atl/reference/iatlmemmgr-class.md)

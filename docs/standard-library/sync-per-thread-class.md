---
title: sync_per_thread 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e366f9b0cf92aed9c61609642f48f0e5cc9530d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="syncperthread-class"></a>sync_per_thread 类

描述为每个线程提供单独的缓存对象的[同步筛选器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`Cache`|与同步筛选器相关联的缓存类型。 它可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

## <a name="remarks"></a>备注

使用 `sync_per_thread` 的分配器可比较相等，尽管不能从一个线程释放另一个线程中分配的块。 使用其中一个分配器时，任一线程中的内存块都不应对其他线程可见。 实际上，这意味着单个线程只能访问使用其中一个分配器的容器。

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[allocate](#allocate)|分配内存块。|
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|
|[equals](#equals)|比较两个缓存是否相等。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="allocate"></a>  sync_per_thread::allocate

分配内存块。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`count`|数组中要分配的元素数目。|

### <a name="remarks"></a>备注

在属于当前线程的缓存对象上，成员函数将返回调用 `cache::allocate(count)` 的结果。 如果没有为当前线程分配任何缓存对象，它首先会分配一个缓存对象。

## <a name="deallocate"></a>  sync_per_thread::deallocate

从指定位置开始从存储中释放指定数量的的对象。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`ptr`|指向要从存储中释放的第一个对象的指针。|
|`count`|要从存储中释放的对象数量。|

### <a name="remarks"></a>备注

在属于当前线程的缓存对象上，成员函数调用 `deallocate`。 如果没有为当前线程分配任何缓存对象，它首先会分配一个缓存对象。

## <a name="equals"></a>  sync_per_thread::equals

比较两个缓存是否相等。

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`Cache`|同步筛选器的缓存对象。|
|`Other`|要用于比较是否相等的缓存对象。|

### <a name="return-value"></a>返回值

如果没有为该对象或当前线程中的 `Other` 分配任何缓存对象，则为 `false`。 否则，它会返回将 `operator==` 应用到两个缓存对象的结果。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

---
title: sync_none 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: 4caf2cc2b6aa7494f343d10709f3190cb41631be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232906"
---
# <a name="sync_none-class"></a>sync_none 类

描述不提供同步的[同步筛选器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|`Cache`|与同步筛选器相关联的缓存类型。 它可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[allocate](#allocate)|分配内存块。|
|[写意](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|
|[equals](#equals)|比较两个缓存是否相等。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a>sync_none：： allocate

分配内存块。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*计数*|数组中要分配的元素数目。|

### <a name="remarks"></a>备注

此成员函数返回 `cache.allocate(count)`，其中 `cache` 是缓存对象。

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a>sync_none：:d eallocate

从指定位置开始从存储中释放指定数量的的对象。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*ptr*|指向要从存储中释放的第一个对象的指针。|
|*计数*|要从存储中释放的对象数量。|

### <a name="remarks"></a>备注

此成员函数调用 `cache.deallocate(ptr, count)`，其中 `cache` 表示缓存对象。

## <a name="sync_noneequals"></a><a name="equals"></a>sync_none：： equals

比较两个缓存是否相等。

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Cache*|同步筛选器的缓存对象。|
|*其他*|要用于比较是否相等的缓存对象。|

### <a name="return-value"></a>返回值

成员函数总是返回 **`true`** 。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[\<allocators>](../standard-library/allocators-header.md)

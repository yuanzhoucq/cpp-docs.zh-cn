---
title: sync_shared 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
ms.openlocfilehash: 029edea59f29534491232d5d99353ccb093447bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376527"
---
# <a name="sync_shared-class"></a>sync_shared 类

介绍[同步筛选器](../standard-library/allocators-header.md)，它使用互斥体来控制对所有分配器共享的缓存对象的访问。

## <a name="syntax"></a>语法

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*缓存*|与同步筛选器相关联的缓存类型。 它可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[分配](#allocate)|分配内存块。|
|[去分配](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|
|[equals](#equals)|比较两个缓存是否相等。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a>sync_shared：：分配

分配内存块。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*count*|数组中要分配的元素数目。|

### <a name="return-value"></a>返回值

指向已分配对象的指针。

### <a name="remarks"></a>备注

成员函数会锁定互斥体，调用 `cache.allocate(count)`、解除对互斥体的锁定并返回之前调用 `cache.allocate(count)` 的结果。 `cache` 表示当前缓存对象。

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a>sync_shared：:d分配

从指定位置开始从存储中释放指定数量的的对象。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Ptr*|指向要从存储中释放的第一个对象的指针。|
|*count*|要从存储中释放的对象数量。|

### <a name="remarks"></a>备注

此成员函数会锁定互斥体，调用 `cache.deallocate(ptr, count)`其中 `cache` 表示缓存对象），然后取消对该互斥体的锁定。

## <a name="sync_sharedequals"></a><a name="equals"></a>sync_shared：等于

比较两个缓存是否相等。

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*缓存*|与同步筛选器相关联的缓存类型。|
|*其他*|要比较是否相等的缓存。|

### <a name="return-value"></a>返回值

如果 的结果`cache.equals(Other.cache)``cache`表示缓存对象为**true，****则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[\<分配器>](../standard-library/allocators-header.md)

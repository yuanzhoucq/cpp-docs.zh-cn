---
title: rts_alloc 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: f422b171c14695a1207a30419a10d50cdfb5adf0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228123"
---
# <a name="rts_alloc-class"></a>rts_alloc 类

Rts_alloc 类模板描述了一个[筛选器，该筛选器](../standard-library/allocators-header.md)保存缓存实例的数组，并确定在运行时（而不是在编译时）用于分配和解除分配的实例。

## <a name="syntax"></a>语法

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Cache*|数组中包含的缓存实例的类型。 这可能是 [cache_chunklist 类](../standard-library/cache-chunklist-class.md)、 [cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

## <a name="remarks"></a>备注

此类模板包含多个块分配器实例，并确定在运行时（而不是在编译时）用于分配或解除分配的实例。 它与不能编译重新绑定的编译器一起使用。

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[allocate](#allocate)|分配内存块。|
|[写意](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|
|[equals](#equals)|比较两个缓存是否相等。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc：： allocate

分配内存块。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*计数*|数组中要分配的元素数目。|

### <a name="return-value"></a>返回值

指向已分配对象的指针。

### <a name="remarks"></a>备注

成员函数返回 `caches[_IDX].allocate(count)` ，其中索引由 `_IDX` 所请求的块大小*计数*确定，如果*count*太大，则返回 `operator new(count)` 。 用于表示缓存对象的 `cache`。

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc：:d eallocate

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

成员函数将调用 `caches[_IDX].deallocate(ptr, count)` ，其中索引由 `_IDX` 所请求的块大小*计数*确定，如果*count*太大，则返回 `operator delete(ptr)` 。

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc：： equals

比较两个缓存是否相等。

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*_Cache*|与筛选器关联的缓存对象。|
|*_Other*|要用于比较是否相等的缓存对象。|

### <a name="remarks"></a>备注

**`true`** 如果的结果 `caches[0].equals(other.caches[0])` ，则为; 否则为 **`false`** 。 `caches` 表示缓存对象的数组。

## <a name="see-also"></a>另请参阅

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)

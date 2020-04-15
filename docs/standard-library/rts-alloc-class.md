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
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373426"
---
# <a name="rts_alloc-class"></a>rts_alloc 类

rts_alloc类模板描述一个[筛选器](../standard-library/allocators-header.md)，该筛选器包含缓存实例数组，并确定在运行时而不是在编译时使用哪个实例进行分配和分配。

## <a name="syntax"></a>语法

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*缓存*|数组中包含的缓存实例的类型。 这可能是 [cache_chunklist 类](../standard-library/cache-chunklist-class.md)、 [cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

## <a name="remarks"></a>备注

此类模板包含多个块分配器实例，并确定在运行时而不是在编译时使用哪个实例进行分配或分配。 它与不能编译重新绑定的编译器一起使用。

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[分配](#allocate)|分配内存块。|
|[去分配](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|
|[equals](#equals)|比较两个缓存是否相等。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc：：分配

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

成员函数`caches[_IDX].allocate(count)`返回 ，其中索引`_IDX`由请求的块大小*计数*确定，或者，如果*计数*太大，则返回`operator new(count)`。 用于表示缓存对象的 `cache`。

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc：:d分配

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

成员函数`caches[_IDX].deallocate(ptr, count)`调用 ，其中索引`_IDX`由请求的块大小*计数*确定，或者，如果*计数*太大，则返回`operator delete(ptr)`。

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc：等于

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

**如果 为** `caches[0].equals(other.caches[0])`，则 为否则，**假**。 `caches` 表示缓存对象的数组。

## <a name="see-also"></a>另请参阅

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<分配器>](../standard-library/allocators-header.md)

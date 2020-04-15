---
title: cache_suballoc 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 55860a65fc77f834ed699f3a5114768b7efdde6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366722"
---
# <a name="cache_suballoc-class"></a>cache_suballoc 类

定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*深圳*|数组中要分配的元素数目。|

## <a name="remarks"></a>备注

cache_suballoc类模板将处理位置的内存块存储在具有无界长度的可用列表中，使用`freelist<sizeof(Type), max_unbounded>`，并在空闲列表为空时从与**运算符新**分配的较大块中分配内存块。

每个区块`Sz * Nelts`都保存可用内存的字节以及**运算符新**和**运算符删除**所需的数据。 不会释放已分配的区块。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[cache_suballoc](#cache_suballoc)|构造 `cache_suballoc` 类型的对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[分配](#allocate)|分配内存块。|
|[去分配](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a>cache_suballoc：：分配

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a>cache_suballoc：cache_suballoc

构造 `cache_suballoc` 类型的对象。

```cpp
cache_suballoc();
```

### <a name="remarks"></a>备注

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a>cache_suballoc：:d分配

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

## <a name="see-also"></a>另请参阅

[\<分配器>](../standard-library/allocators-header.md)

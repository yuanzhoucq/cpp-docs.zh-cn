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
ms.openlocfilehash: 06d0ef390e6ae1980b9ab20b8ceb67213837148b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438865"
---
# <a name="cachesuballoc-class"></a>cache_suballoc 类

定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*sz*|数组中要分配的元素数目。|

## <a name="remarks"></a>备注

Cache_suballoc 模板类将释放的内存块存储在长度不受限制的可用列表中使用`freelist<sizeof(Type), max_unbounded>`，并使用分配的较大区块中细分内存块**new 运算符**空闲列表时为空。

每个区块保留`Sz * Nelts`字节的可用内存和数据的**new 运算符**并**运算符 delete**要求。 不会释放已分配的区块。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[cache_suballoc](#cache_suballoc)|构造 `cache_suballoc` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[allocate](#allocate)|分配内存块。|
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

分配内存块。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*count*|数组中要分配的元素数目。|

### <a name="return-value"></a>返回值

指向已分配对象的指针。

### <a name="remarks"></a>备注

## <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc

构造 `cache_suballoc` 类型的对象。

```cpp
cache_suballoc();
```

### <a name="remarks"></a>备注

## <a name="deallocate"></a>  cache_suballoc::deallocate

从指定位置开始从存储中释放指定数量的的对象。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*ptr*|指向要从存储中释放的第一个对象的指针。|
|*count*|要从存储中释放的对象数量。|

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

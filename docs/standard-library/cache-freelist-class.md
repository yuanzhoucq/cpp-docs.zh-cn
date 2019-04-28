---
title: cache_freelist 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: 56fdfb191f9208a5ffa692e1d599545ddeaeb36c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352107"
---
# <a name="cachefreelist-class"></a>cache_freelist 类

定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Sz*|数组中要分配的元素数目。|
|*最大值*|表示释放列表的最大大小的 max 类。 其可以是 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>备注

Cache_freelist 模板类维持大小的内存块释放列表*Sz*。 当释放列表已满时它使用**运算符 delete**释放内存块。 当释放列表为空时它使用**运算符 new**来分配新的内存块。 空闲列表的最大大小由传递的 max 类的类*最大*参数。

每个内存块保留*Sz*字节的可用内存和数据的**运算符 new**并**运算符 delete**要求。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[cache_freelist](#cache_freelist)|构造 `cache_freelist` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[allocate](#allocate)|分配内存块。|
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="allocate"></a>  cache_freelist::allocate

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

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

构造 `cache_freelist` 类型的对象。

```cpp
cache_freelist();
```

### <a name="remarks"></a>备注

## <a name="deallocate"></a>  cache_freelist::deallocate

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

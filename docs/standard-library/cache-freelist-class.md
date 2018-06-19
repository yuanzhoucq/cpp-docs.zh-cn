---
title: cache_freelist 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8478490914a6f9049cd54ec78c8de8a1e519f36f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845669"
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
|`Sz`|数组中要分配的元素数目。|
|`Max`|表示释放列表的最大大小的 max 类。 其可以是 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>备注

cache_freelist 模板类维持大小为 `Sz` 的内存块释放列表。 当释放列表已满时，其使用 `operator delete` 释放内存块。 当释放列表为空时，其使用 `operator new` 分配新的内存块。 释放列表的最大大小由 `Max` 参数传递的 max 类决定。

每个内存块保留 `Sz` 个字节的可用内存和 `operator new` 及 `operator delete` 所需的数据。

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
|`count`|数组中要分配的元素数目。|

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
|`ptr`|指向要从存储中释放的第一个对象的指针。|
|`count`|要从存储中释放的对象数量。|

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

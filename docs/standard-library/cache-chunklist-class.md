---
title: cache_chunklist 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366759"
---
# <a name="cache_chunklist-class"></a>cache_chunklist 类

定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*深圳*|数组中要分配的元素数目。|

## <a name="remarks"></a>备注

类模板使用**新运算符**来分配原始内存块，根据需要为内存块分配存储的子分配块;它将处理的内存块存储在每个块的单独可用列表中，并使用**运算符删除**在其内存块未使用时解分配块。

每个内存块都保存可用内存的*Sz*字节和指向其所属块的指针。 每个块包含`Nelts`内存块、三个指针、int 以及**操作员新**数据和**运算符删除**所需的数据。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[cache_chunklist](#cache_chunklist)|构造 `cache_chunklist` 类型的对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[分配](#allocate)|分配内存块。|
|[去分配](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist：分配

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist：cache_chunklist

构造 `cache_chunklist` 类型的对象。

```cpp
cache_chunklist();
```

### <a name="remarks"></a>备注

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist：:d分配

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

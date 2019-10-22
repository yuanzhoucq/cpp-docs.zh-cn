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
ms.openlocfilehash: 035e5153b4e4c84743a64bcc9cec24920a6a0336
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688366"
---
# <a name="cache_chunklist-class"></a>cache_chunklist 类

定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Sz*|数组中要分配的元素数目。|

## <a name="remarks"></a>备注

此类模板使用**new 运算符**来分配原始内存块，suballocating 块在需要时为内存块分配存储;它将已释放的内存块存储在单独的可用列表中，用于每个块区，并在不使用任何内存块时使用**运算符 delete**解除块。

每个内存块都包含*Sz*字节的可用内存和指向其所属块区的指针。 每个区块都包含 `Nelts` 内存块、三个指针、一个 int 以及**运算符 new**和**operator delete**需要的数据。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[cache_chunklist](#cache_chunklist)|构造 `cache_chunklist` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[allocate](#allocate)|分配内存块。|
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

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

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

构造 `cache_chunklist` 类型的对象。

```cpp
cache_chunklist();
```

### <a name="remarks"></a>备注

## <a name="deallocate"></a>  cache_chunklist::deallocate

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

[\<allocators>](../standard-library/allocators-header.md)

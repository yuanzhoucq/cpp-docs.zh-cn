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
ms.openlocfilehash: 94ae4dfc8f5f9073c0a39f315adfbed3e5c14daf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594566"
---
# <a name="cachechunklist-class"></a>cache_chunklist 类

定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*sz*|数组中要分配的元素数目。|

## <a name="remarks"></a>备注

使用此模板类**运算符 new**分配原始内存的区块，并阻止分配的内存块时所需的存储; 它将释放的内存块存储在每个区块的独立释放列表并使用**运算符 delete**时正在使用中的任何内存块释放区块。

每个内存块保留*Sz*个字节的可用内存以及指向其所属的块区的指针。 每个区块保留`Nelts`内存块、 三个指针、 整数和数据的**new 运算符**并**运算符 delete**要求。

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

**标头：**\<allocators>

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

[\<allocators>](../standard-library/allocators-header.md)<br/>

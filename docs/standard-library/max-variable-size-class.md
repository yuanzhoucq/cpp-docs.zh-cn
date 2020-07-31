---
title: max_variable_size 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: f98b5698ff14349abf9300799f00c6d9121bcf65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222259"
---
# <a name="max_variable_size-class"></a>max_variable_size 类

描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象限制为与已分配的内存块数大致成比例的最大长度。

## <a name="syntax"></a>语法

```cpp
class max_variable_size
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[max_variable_size](#max_variable_size)|构造 `max_variable_size` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[分配](#allocated)|逐量增加已分配的内存块的计数。|
|[分配](#deallocated)|逐量减小已分配的内存块的计数。|
|[full](#full)|返回一个值，该值指定是否应将更多的内存块添加到空闲列表。|
|[取出](#released)|逐量减小空闲列表上内存块的计数。|
|[saved](#saved)|逐量增加空闲列表上内存块的计数。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size：：已分配

逐量增加已分配的内存块的计数。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数将 *_Nx*添加到存储值 `_Nallocs` 。 此成员函数在每次成功调用后调用 `cache_freelist::allocate` 到运算符 **`new`** 。 参数 *_Nx*是由运算符分配的块区中的内存块数 **`new`** 。

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size：:d eallocated

逐量减小已分配的内存块的计数。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

成员函数从存储 *_Nx*的值中减去 _Nx `_Nallocs` 。 此成员函数在每次调用后调用 `cache_freelist::deallocate` 到运算符 **`delete`** 。 参数 *_Nx*是由运算符释放的块区中的内存块数 **`delete`** 。

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size：： full

返回一个值，该值指定是否应将更多的内存块添加到空闲列表。

```cpp
bool full();
```

### <a name="return-value"></a>返回值

**`true`** 如果为 `_Nallocs / 16 + 16 <= _Nblocks` 。

### <a name="remarks"></a>备注

此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回，则将 **`true`** `deallocate` 内存块置于可用列表中; 如果返回 false，则 `deallocate` 调用运算符 **`delete`** 来释放块。

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size：： max_variable_size

构造 `max_variable_size` 类型的对象。

```cpp
max_variable_size();
```

### <a name="remarks"></a>备注

该构造函数将存储的值 `_Nblocks` 和 `_Nallocs` 初始化为零。

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size：：已发布

逐量减小空闲列表上内存块的计数。

```cpp
void released();
```

### <a name="remarks"></a>备注

此成员函数逐量减小存储值 `_Nblocks`。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size：：已保存

逐量增加空闲列表上内存块的计数。

```cpp
void saved();
```

### <a name="remarks"></a>备注

此成员函数逐量增加存储值 `_Nblocks`。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。

## <a name="see-also"></a>另请参阅

[\<allocators>](../standard-library/allocators-header.md)

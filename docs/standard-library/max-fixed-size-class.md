---
title: max_fixed_size 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 08510ecc3b7469e8f88a61dcb0df28541e170892
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412951"
---
# <a name="maxfixedsize-class"></a>max_fixed_size 类

描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象的最大长度限制为固定的最大长度。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*最大值*|max 类，用于决定要存储于 `freelist` 中的最大元素数目。|

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[max_fixed_size](#max_fixed_size)|构造 `max_fixed_size` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[allocated](#allocated)|逐量增加已分配的内存块的计数。|
|[deallocated](#deallocated)|逐量减小已分配的内存块的计数。|
|[full](#full)|返回一个值，该值指定是否应将更多的内存块添加到空闲列表。|
|[released](#released)|逐量减小空闲列表上内存块的计数。|
|[saved](#saved)|逐量增加空闲列表上内存块的计数。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="allocated"></a>max_fixed_size::allocated

逐量增加已分配的内存块的计数。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 在每次调用成功后，调用此成员函数`cache_freelist::allocate`向操作员**新**。 自变量 *_Nx*是由运算符分配的区块中的内存块的数目**新**。

## <a name="deallocated"></a>max_fixed_size::deallocated

逐量减小已分配的内存块的计数。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 通过每次调用后调用此成员函数`cache_freelist::deallocate`向操作员**删除**。 自变量 *_Nx*是由运算符解除分配的区块中的内存块的数目**删除**。

## <a name="full"></a>max_fixed_size::full

返回一个值，该值指定是否应将更多的内存块添加到空闲列表。

```cpp
bool full();
```

### <a name="return-value"></a>返回值

**true**如果`Max <= _Nblocks`; 否则为**false**。

### <a name="remarks"></a>备注

此成员函数由 `cache_freelist::deallocate` 调用。 如果该调用将返回 **，则返回 true**，`deallocate`放入内存块释放列表; 如果它返回 false，`deallocate`调用运算符**删除**解除分配块。

## <a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

构造 `max_fixed_size` 类型的对象。

```cpp
max_fixed_size();
```

### <a name="remarks"></a>备注

该构造函数将存储的值 `_Nblocks` 初始化为零。

## <a name="released"></a>max_fixed_size::released

逐量减小空闲列表上内存块的计数。

```cpp
void released();
```

### <a name="remarks"></a>备注

逐量减小存储值 `_Nblocks`。 每当当前 [max 类](../standard-library/allocators-header.md)的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。

## <a name="saved"></a>max_fixed_size::saved

逐量增加空闲列表上内存块的计数。

```cpp
void saved();
```

### <a name="remarks"></a>备注

此成员函数逐量增加存储值 `_Nblocks`。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

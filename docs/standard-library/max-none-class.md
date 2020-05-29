---
title: max_none 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: c49ceec72be62d8ff3125f04d97bbb6952501677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370980"
---
# <a name="max_none-class"></a>max_none 类

描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象的最大长度限制为零。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*麦克斯*|max 类，用于决定要存储于 `freelist` 中的最大元素数目。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[分配](#allocated)|逐量增加已分配的内存块的计数。|
|[交易](#deallocated)|逐量减小已分配的内存块的计数。|
|[full](#full)|返回一个值，该值指定是否应将更多的内存块添加到空闲列表。|
|[释放](#released)|逐量减小空闲列表上内存块的计数。|
|[saved](#saved)|逐量增加空闲列表上内存块的计数。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="max_noneallocated"></a><a name="allocated"></a>max_none：：已分配

逐量增加已分配的内存块的计数。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 它调用后，每次成功调用`cache_freelist::allocate`到运算符**新**。 *参数_Nx*是运算符**new**分配块中的内存块数。

## <a name="max_nonedeallocated"></a><a name="deallocated"></a>max_none：:d分配

逐量减小已分配的内存块的计数。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 此成员函数在每次调用后调用`cache_freelist::deallocate`运算符**删除**后调用 。 *参数_Nx*是由运算符**删除**处理块中的内存块数。

## <a name="max_nonefull"></a><a name="full"></a>max_none：：完整

返回一个值，该值指定是否应将更多的内存块添加到空闲列表。

```cpp
bool full();
```

### <a name="return-value"></a>返回值

此成员函数始终返回**true**。

### <a name="remarks"></a>备注

此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回**true，** 则将内存块放在空闲列表中;如果调用返回 true，`deallocate`则将内存块放在可用列表中。如果它返回**false** `deallocate` ，则调用运算符**删除**以取消分配块。

## <a name="max_nonereleased"></a><a name="released"></a>max_none：：已发布

逐量减小空闲列表上内存块的计数。

```cpp
void released();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。

## <a name="max_nonesaved"></a><a name="saved"></a>max_none：：已保存

逐量增加空闲列表上内存块的计数。

```cpp
void saved();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。

## <a name="see-also"></a>另请参阅

[\<分配器>](../standard-library/allocators-header.md)

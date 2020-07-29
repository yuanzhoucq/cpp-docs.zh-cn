---
title: max_unbounded 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: 8ec0f1c6c84399ef4b3d048a99d1c191541b7c6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222272"
---
# <a name="max_unbounded-class"></a>max_unbounded 类

描述 [max 类](../standard-library/allocators-header.md) 对象，该对象不限制 [freelist](../standard-library/freelist-class.md) 对象的最大长度。

## <a name="syntax"></a>语法

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a>max_unbounded：：已分配

逐量增加已分配的内存块的计数。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 它在每次成功调用后调用 `cache_freelist::allocate` 到运算符 **`new`** 。 参数 *_Nx*是由运算符分配的块区中的内存块数 **`new`** 。

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a>max_unbounded：:d eallocated

逐量减小已分配的内存块的计数。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 此成员函数在每次调用后调用 `cache_freelist::deallocate` 到运算符 **`delete`** 。 参数 *_Nx*是由运算符释放的块区中的内存块数 **`delete`** 。

## <a name="max_unboundedfull"></a><a name="full"></a>max_unbounded：： full

返回一个值，该值指定是否应将更多的内存块添加到空闲列表。

```cpp
bool full();
```

### <a name="return-value"></a>返回值

成员函数总是返回 **`false`** 。

### <a name="remarks"></a>备注

此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回，则将 **`true`** `deallocate` 内存块置于可用列表中; 如果返回 false，则 `deallocate` 调用运算符 **`delete`** 来释放块。

## <a name="max_unboundedreleased"></a><a name="released"></a>max_unbounded：：已发布

逐量减小空闲列表上内存块的计数。

```cpp
void released();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。

## <a name="max_unboundedsaved"></a><a name="saved"></a>max_unbounded：：已保存

逐量增加空闲列表上内存块的计数。

```cpp
void saved();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。

## <a name="see-also"></a>另请参阅

[\<allocators>](../standard-library/allocators-header.md)

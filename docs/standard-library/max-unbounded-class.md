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
ms.openlocfilehash: ba99d6ed3af34363bf88cde1a40e4bf37841cd8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412912"
---
# <a name="maxunbounded-class"></a>max_unbounded 类

描述 [max 类](../standard-library/allocators-header.md) 对象，该对象不限制 [freelist](../standard-library/freelist-class.md) 对象的最大长度。

## <a name="syntax"></a>语法

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>max_unbounded::allocated

逐量增加已分配的内存块的计数。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Nx*|增量值。|

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每次调用成功后，它将调用`cache_freelist::allocate`向操作员**新**。 自变量 *_Nx*是由运算符分配的区块中的内存块的数目**新**。

## <a name="deallocated"></a>max_unbounded::deallocated

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

## <a name="full"></a>max_unbounded::full

返回一个值，该值指定是否应将更多的内存块添加到空闲列表。

```cpp
bool full();
```

### <a name="return-value"></a>返回值

成员函数总是返回**false**。

### <a name="remarks"></a>备注

此成员函数由 `cache_freelist::deallocate` 调用。 如果该调用将返回 **，则返回 true**，`deallocate`放入内存块释放列表; 如果它返回 false，`deallocate`调用运算符**删除**解除分配块。

## <a name="released"></a>max_unbounded::released

逐量减小空闲列表上内存块的计数。

```cpp
void released();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。

## <a name="saved"></a>max_unbounded::saved

逐量增加空闲列表上内存块的计数。

```cpp
void saved();
```

### <a name="remarks"></a>备注

此成员函数不执行任何操作。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

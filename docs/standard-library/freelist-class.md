---
title: freelist 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: e37b2371238211033d6a8a0847a41677b4e908a2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688043"
---
# <a name="freelist-class"></a>freelist 类

管理内存块列表。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Sz*|数组中要分配的元素数目。|
|*最大值*|max 类表示可存储在空闲列表中的元素的最大数量。 max 类可以是 [max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>备注

此类模板管理一个大小为*Sz*的内存块列表，该列表的最大长度由最大传入的 max 类*确定。*

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[freelist](#freelist)|构造 `freelist` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[pop](#pop)|从空闲列表中删除第一个内存块。|
|[push](#push)|向列表中添加内存块。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="freelist"></a>  freelist::freelist

构造 `freelist` 类型的对象。

```cpp
freelist();
```

### <a name="remarks"></a>备注

## <a name="pop"></a>  freelist::pop

从空闲列表中删除第一个内存块。

```cpp
void *pop();
```

### <a name="return-value"></a>返回值

返回指向从列表中删除的内存块的指针。

### <a name="remarks"></a>备注

如果列表为空，则成员函数返回 NULL。 否则，成员函数从列表中删除第一个内存块。

## <a name="push"></a>  freelist::push

向列表中添加内存块。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*ptr*|指向要添加到空闲列表的内存块的指针。|

### <a name="return-value"></a>返回值

如果 max 类的 `full` 函数返回**false**，则**为 true** ;否则，`push` 函数将返回**false**。

### <a name="remarks"></a>备注

如果 max 类的 `full` 函数返回**false**，则此成员函数会将由*ptr*指向的内存块添加到列表的开头。

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

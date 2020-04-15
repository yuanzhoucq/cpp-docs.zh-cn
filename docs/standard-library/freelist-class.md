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
ms.openlocfilehash: 712c1f1638b954d1580eb527dd9eab7401917517
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317209"
---
# <a name="freelist-class"></a>freelist 类

管理内存块列表。

## <a name="syntax"></a>语法

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*深圳*|数组中要分配的元素数目。|
|*麦克斯*|max 类表示可存储在空闲列表中的元素的最大数量。 max 类可以是 [max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>备注

此类模板管理大小*Sz*的内存块列表，该列表的最大长度由*Max*中传递的最大类确定。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[freelist](#freelist)|构造 `freelist` 类型的对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[流行](#pop)|从空闲列表中删除第一个内存块。|
|[推](#push)|向列表中添加内存块。|

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>自由列表：：免费列表

构造 `freelist` 类型的对象。

```cpp
freelist();
```

### <a name="remarks"></a>备注

## <a name="freelistpop"></a><a name="pop"></a>自由列表：:pop

从空闲列表中删除第一个内存块。

```cpp
void *pop();
```

### <a name="return-value"></a>返回值

返回指向从列表中删除的内存块的指针。

### <a name="remarks"></a>备注

如果列表为空，则成员函数返回 NULL。 否则，成员函数从列表中删除第一个内存块。

## <a name="freelistpush"></a><a name="push"></a>自由名单：:p

向列表中添加内存块。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Ptr*|指向要添加到空闲列表的内存块的指针。|

### <a name="return-value"></a>返回值

**如果**最大类`full`的函数返回**false，** 则为 true ;否则，`push`函数将返回**false**。

### <a name="remarks"></a>备注

如果`full`max 类的函数返回**false，** 则此成员函数会将*ptr*指向的内存块添加到列表的头部。

## <a name="see-also"></a>另请参阅

[\<分配器>](../standard-library/allocators-header.md)

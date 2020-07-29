---
title: sync_per_container 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: d38307c4ae19e5f87d0dbcca8943dc1c3f239917
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232893"
---
# <a name="sync_per_container-class"></a>sync_per_container 类

描述为每个筛选器对象提供单独的缓存对象的[同步筛选](../standard-library/allocators-header.md) 。

## <a name="syntax"></a>语法

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Cache*|与同步筛选器相关联的缓存类型。 它可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[equals](#equals)|比较两个缓存是否相等。|

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a>sync_per_container：： equals

比较两个缓存是否相等。

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Cache*|同步筛选器的缓存对象。|
|*其他*|要用于比较是否相等的缓存对象。|

### <a name="return-value"></a>返回值

成员函数总是返回 **`false`** 。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[\<allocators>](../standard-library/allocators-header.md)

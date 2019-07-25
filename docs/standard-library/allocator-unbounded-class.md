---
title: allocator_unbounded 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 38ecec3848808585ac0ed7cb1b076480a79f6d41
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448302"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded 类

描述一个对象, 该*对象使用类型*为[cache_freelist](../standard-library/cache-freelist-class.md)的缓存 (其长度由[max_unbounded](../standard-library/max-unbounded-class.md)管理) 来管理类型为 type 的对象的存储分配和释放。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Type*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

在以下语句中, [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将此类作为*name*参数传递:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

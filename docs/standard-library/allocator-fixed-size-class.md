---
title: allocator_fixed_size 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
ms.openlocfilehash: 5ee506838ea723b82f04bba301c19c0149d986bf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451001"
---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size 类

描述一个对象, 该*对象使用类型*为[cache_freelist](../standard-library/cache-freelist-class.md)的缓存 (其长度由[max_fixed_size](../standard-library/max-fixed-size-class.md)管理) 来管理类型为 type 的对象的存储分配和释放。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Type*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

在以下语句中, [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将此类作为*name*参数传递:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

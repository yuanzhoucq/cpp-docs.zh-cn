---
title: allocator_suballoc 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 3e5b69ef3f47a173ef768283bbae4f6e3b5f5190
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458141"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc 类

描述一个对象, 该对象使用类型为[cache_suballoc](../standard-library/cache-suballoc-class.md)的缓存管理类型为*type*的对象的存储分配和释放。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Type*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

在以下语句中, [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将此类作为*name*参数传递:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

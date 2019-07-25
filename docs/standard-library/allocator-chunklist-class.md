---
title: allocator_chunklist 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 46ae9c613b66e00658f09ad10f33b721c6948ff7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456427"
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist 类

描述一个对象，用于管理使用缓存类型为 [cache_chunklist](../standard-library/cache-chunklist-class.md) 的对象的存储分配和释放。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Type*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

在以下语句中, [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将此类作为*name*参数传递:`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

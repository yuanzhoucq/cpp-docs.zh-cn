---
title: allocator_suballoc 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 9136a2ce744e19754b3a660e7bc9c15f05babbbf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610647"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc 类

描述一个对象，用于管理存储分配和释放的对象的类型*类型*使用缓存类型[cache_suballoc](../standard-library/cache-suballoc-class.md)。

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

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将作为此类传递*名称*以下语句中的参数： `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

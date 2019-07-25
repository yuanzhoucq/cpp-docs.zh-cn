---
title: allocator_newdel 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: d49a1596371e4a69873b826d3e756f263539d034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448312"
---
# <a name="allocatornewdel-class"></a>allocator_newdel 类

实现一个分配器, 该分配器使用**运算符 delete**来释放内存块, 使用**new 运算符**分配内存块。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Type*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

在以下语句中, [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将此类作为*name*参数传递:`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>要求

**标头：** \<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)

---
title: allocator_variable_size 类
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: a2c4681ec5252166754a45b026ea119651f18a38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371645"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size 类

描述一个对象，用于管理存储分配和释放的对象的类型*类型*使用缓存类型[cache_freelist](../standard-library/cache-freelist-class.md)长度由[max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Type*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将作为此类传递*名称*以下语句中的参数： `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

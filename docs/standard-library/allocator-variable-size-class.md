---
title: allocator_variable_size 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 690be271cd7e9ad3eaf019f1feb67202c14a9e5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840597"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size 类

描述一个对象，用于管理使用缓存类型为 [cache_freelist](../standard-library/cache-freelist-class.md) 的对象类型 `Type` 的存储分配和释放，其长度由 [max_variable_size](../standard-library/max-variable-size-class.md) 管理。

## <a name="syntax"></a>语法

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`Type`|由分配器分配元素类型。|

## <a name="remarks"></a>备注

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 宏将此类传递为以下语句中的 `name` 参数：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

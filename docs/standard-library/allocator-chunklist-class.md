---
title: allocator_chunklist 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20e601608b1a6b0f076040c10e027f7dc78db17a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955353"
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
|*类型*|由分配器分配元素类型。|

## <a name="remarks"></a>备注

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏将作为此类传递*名称*以下语句中的参数： `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>要求

**标头：**\<allocators>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)<br/>

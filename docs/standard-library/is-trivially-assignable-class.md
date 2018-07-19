---
title: is_trivially_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47fabb7120cc13eeca38bc9d06428f686fc9f1b9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955561"
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable 类

测试 `From` 类型的值是否能够普通赋予 `To` 类型

## <a name="syntax"></a>语法

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>参数

为接受赋值的对象的类型。

从提供的值的对象的类型。

## <a name="remarks"></a>备注

表达式 `declval<To>() = declval<From>()` 必须格式正确，且编译器必须已知其不需要任何重要操作。 这两`From`并`To`必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

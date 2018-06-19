---
title: is_trivially_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757a5eb526bc8d4294a64cbdc9645e72285162ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857254"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 类

测试使用指定参数类型时类型是否为普通构造类型。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>参数

`T` 查询的类型。

`Args` 要匹配的构造函数中的自变量类型`T`。

## <a name="remarks"></a>备注

如果通过使用 `Args` 中的参数类型可普通构造类型 `T`，则类型谓词的实例为 true；否则为 false。 如果变量定义 `T t(std::declval<Args>()...);` 格式正确且已知其不会调用任何重要的操作，则类型 `T` 为普通构造类型。 `T` 和 `Args` 中的所有类型都必须是完整类型、`void` 或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

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
ms.openlocfilehash: f73559503ad427c9b7eb513d4164d3348c652948
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954742"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 类

测试使用指定参数类型时类型是否为普通构造类型。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>参数

*T*查询的类型。

*Args*要匹配的构造函数中的参数类型*T*。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*通过使用中的参数类型为普通构造*Args*，否则为 false。 类型*T*为普通构造如果变量定义`T t(std::declval<Args>()...);`是格式正确，以及确定要调用任何重要的操作。 这两*T*和中的所有类型*Args*必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

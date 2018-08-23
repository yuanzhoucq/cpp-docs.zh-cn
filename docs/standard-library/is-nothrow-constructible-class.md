---
title: is_nothrow_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c4a96224b86cb12af4e3abfed1f02b33e8a2594
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966558"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 类

测试类型是否可构造以及是否已知该类型在使用指定参数类型时不会引发。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>参数

*T*查询的类型。

*Args*要匹配的构造函数中的参数类型*T*。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*通过使用中的参数类型是可构造*Args*，并在构造函数已知由编译器不会引发; 否则为 false。 类型*T*可构造如果变量定义`T t(std::declval<Args>()...);`而言格式是否正确。 这两*T*和中的所有类型*Args*必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

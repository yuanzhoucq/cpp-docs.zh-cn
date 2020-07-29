---
title: is_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: a968efa5a867a3fd0e60594784cdb11122a974b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222402"
---
# <a name="is_constructible-class"></a>is_constructible 类

测试使用指定参数类型时是否可构造类型。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

*Args*\
*T*的构造函数中要匹配的参数类型。

## <a name="remarks"></a>备注

如果类型*T*通过*使用参数类型可构造，则*类型谓词的实例为 true; 否则为 false。 如果变量定义格式正确，则类型*T*为可构造 `T t(std::declval<Args>()...);` 。 *参数*中的*T*和所有类型都必须是完整类型、 **`void`** 或未知绑定的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)

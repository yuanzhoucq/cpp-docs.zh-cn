---
title: is_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: dc0596ac7a3fc2bcbcbe49f5fa4b20a971e5e445
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452866"
---
# <a name="isconstructible-class"></a>is_constructible 类

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

如果类型*T*通过使用参数类型*可构造, 则*类型谓词的实例为 true; 否则为 false。 如果变量定义`T t(std::declval<Args>()...);`格式正确, 则类型 T 为可构造。 *参数*中的*T*和所有类型都必须是完整的类型、 **void**或未知绑定的数组。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

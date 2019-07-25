---
title: is_nothrow_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 7ec4fc3ef5d9a799d5d77124870fbb337061c94c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455995"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 类

测试类型是否可构造以及是否已知该类型在使用指定参数类型时不会引发。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

*Args*\
*T*的构造函数中要匹配的参数类型。

## <a name="remarks"></a>备注

如果类型*T*是使用*参数中的*参数类型可构造的, 则类型谓词的实例将为 true, 并且编译器知道该构造函数不会引发;否则为 false。 如果变量定义`T t(std::declval<Args>()...);`格式正确, 则类型 T 为可构造。 *参数*中的*T*和所有类型都必须是完整的类型、 **void**或未知绑定的数组。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)

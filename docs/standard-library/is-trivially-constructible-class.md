---
title: is_trivially_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 1f835dd348c6ef7f2ca7cd01f04c5afc059a55b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222324"
---
# <a name="is_trivially_constructible-class"></a>is_trivially_constructible 类

测试使用指定参数类型时类型是否为普通构造类型。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

*Args*\
*T*的构造函数中要匹配的参数类型。

## <a name="remarks"></a>备注

如果类型*T*通过使用*Args*中的参数类型完全可构造，则类型谓词的实例为 true; 否则为 false。 如果*T*变量定义 `T t(std::declval<Args>()...);` 格式正确且已知不会调用任何不重要的操作，则类型 T 完全可构造。 *参数*中的*T*和所有类型都必须是完整类型、 **`void`** 或未知绑定的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)

---
title: is_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: c921efd5b7e12873ce986952029ae39f118ad763
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658648"
---
# <a name="isconstructible-class"></a>is_constructible 类

测试使用指定参数类型时是否可构造类型。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

*参数*<br/>
要匹配的构造函数中的参数类型*T*。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*通过使用中的参数类型是可构造*Args*，否则为 false。 类型*T*可构造如果变量定义`T t(std::declval<Args>()...);`而言格式是否正确。 这两*T*和中的所有类型*Args*必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

---
title: is_nothrow_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 9ea11d54d49bf8f6ae6416f9663c2593cc66ea3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664121"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 类

测试类型是否可构造以及是否已知该类型在使用指定参数类型时不会引发。

## <a name="syntax"></a>语法

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

*参数*<br/>
要匹配的构造函数中的参数类型*T*。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*通过使用中的参数类型是可构造*Args*，并在构造函数已知由编译器不会引发; 否则为 false。 类型*T*可构造如果变量定义`T t(std::declval<Args>()...);`而言格式是否正确。 这两*T*和中的所有类型*Args*必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

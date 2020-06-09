---
title: add_const 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: c82a3fac8ef95da9e226ca3e2e9122b3c8774cbf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620833"
---
# <a name="add_const-class"></a>add_const 类

从类型设置常量类型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>参数

*Ty*\
要修改的类型。

## <a name="remarks"></a>备注

如果*Ty*是引用、函数或常量限定类型，则类型修饰符的实例会保留*修改后的*类型，否则为 `const Ty` 。

## <a name="example"></a>示例

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](type-traits.md)\
[remove_const 类](remove-const-class.md)

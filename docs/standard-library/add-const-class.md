---
title: add_const 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: 6f27a8e4bc0bea3a469d46a56e8885dabe5894df
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456585"
---
# <a name="addconst-class"></a>add_const 类

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

*如果* *Ty*是引用、函数或常量限定类型, 则类型修饰符的实例会保留修改后的类型, 否则`const Ty`为。

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

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[remove_const 类](../standard-library/remove-const-class.md)

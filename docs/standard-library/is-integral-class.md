---
title: is_integral 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a367bb06f49dd2c9c64f0c257a3573add5645efe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456243"
---
# <a name="isintegral-class"></a>is_integral 类

测试类型是否为整型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*为整型类型之一, 或`cv-qualified`类型为整数类型之一的形式, 则类型谓词的实例为 true; 否则为 false。

整型类型为**bool**、 **char**、**无符号 char**、**有符号 char**、 **wchar_t**、 **short**、**无符号 short**、 **int**、**无符号 int**、 **long**和**无符号长长**。 此外, 对于提供这些方法的编译器, 整型类型可以是**长**、**无符号长**、 **__int64**和**无符号 __int64**。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[is_enum 类](../standard-library/is-enum-class.md)\
[is_floating_point 类](../standard-library/is-floating-point-class.md)

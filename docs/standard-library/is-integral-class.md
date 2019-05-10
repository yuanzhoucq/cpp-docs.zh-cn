---
title: is_integral 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: c7d0d8b8572c26bfa75b9fab81900c0ae21fb932
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336488"
---
# <a name="isintegral-class"></a>is_integral 类

测试类型是否为整型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是一种整型类型，或`cv-qualified`窗体的一种整型类型，否则为保留为 false。

一种整型类型是之一**bool**， **char**， **unsigned char**，**签名 char**， **wchar_t**， **短**， **unsigned short**， **int**，**无符号的 int**，**长**，和**无符号长**。 此外，向他们提供的编译器，整型类型可以是之一**超长**， **unsigned long long**， **__int64**，和**unsigned 的 __int64**.

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

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum 类](../standard-library/is-enum-class.md)<br/>
[is_floating_point 类](../standard-library/is-floating-point-class.md)<br/>

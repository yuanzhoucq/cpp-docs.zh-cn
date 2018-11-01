---
title: is_convertible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_convertible
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
ms.openlocfilehash: 1df87299d0b06ccfd2bef05bab89a9241f27d57d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583551"
---
# <a name="isconvertible-class"></a>is_convertible 类

测试一种类型是否可转换为另一种类型。

## <a name="syntax"></a>语法

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>参数

*From*<br/>
要转换的类型。

*Ty*<br/>
要转换为的类型。

## <a name="remarks"></a>备注

如果表达式 `To to = from;`（其中 `from` 是类型 `From` 的对象）为标准的格式，则类型谓词的实例将为 true。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }

```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_base_of 类](../standard-library/is-base-of-class.md)<br/>

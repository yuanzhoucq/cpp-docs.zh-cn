---
title: is_object 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_object
helpviewer_keywords:
- is_object class
- is_object
ms.assetid: b452ceea-5676-488f-925b-ab881126c387
ms.openlocfilehash: 89c554bda1c82fbedda5b027dbb70b12c2c7cec4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413642"
---
# <a name="isobject-class"></a>is_object 类

测试类型是否为对象类型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_object;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 false 类型*Ty*是引用类型、 函数类型或 void、 或`cv-qualified`窗体的其中之一，否则保持为 true。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_object.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_object<trivial> == " << std::boolalpha
        << std::is_object<trivial>::value << std::endl;
    std::cout << "is_object<functional> == " << std::boolalpha
        << std::is_object<functional>::value << std::endl;
    std::cout << "is_object<trivial&> == " << std::boolalpha
        << std::is_object<trivial&>::value << std::endl;
    std::cout << "is_object<float()> == " << std::boolalpha
        << std::is_object<float()>::value << std::endl;
    std::cout << "is_object<void> == " << std::boolalpha
        << std::is_object<void>::value << std::endl;

    return (0);
    }
```

```Output
is_object<trivial> == true
is_object<functional> == true
is_object<trivial&> == false
is_object<float()> == false
is_object<void> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_function 类](../standard-library/is-function-class.md)<br/>

---
title: add_volatile 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: e8c213a116ff7a7d4218179f0e944ac4f84a75e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230267"
---
# <a name="add_volatile-class"></a>add_volatile 类

**`volatile`** 从指定类型创建类型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>参数

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

`add_volatile<T>` **`typedef`** `type` 如果*t*是引用、函数或可变限定类型，则实例的成员为*t* ，否则为 **`volatile`** *t*。别名 `add_volatile_t` 是访问成员的快捷方式 **`typedef`** `type` 。

## <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](type-traits.md)\
[remove_volatile 类](remove-volatile-class.md)

---
title: add_volatile 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: becea4ff52342a79d0b87ffe0022e2cf84c47949
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456537"
---
# <a name="addvolatile-class"></a>add_volatile 类

从指定类型创建**可变**类型。

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

如果 t 是`add_volatile<T>`引用、函数或可变限定类型, 则实例的成员**typedef** `type`为*T* , 否则为**volatile** *t*。别名`add_volatile_t`是访问成员**typedef** `type`的快捷方式。

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

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[remove_volatile 类](../standard-library/remove-volatile-class.md)

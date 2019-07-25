---
title: add_lvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_lvalue_reference
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
ms.openlocfilehash: 6317b6665adb7f3a06da564fcf049d0b64eb42e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456561"
---
# <a name="addlvaluereference-class"></a>add_lvalue_reference 类

从类型设置对类型的引用。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_lvalue_reference;

template <class T>
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;
```

### <a name="parameters"></a>参数

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

*如果* *t*是左值引用, 则类型修饰符的实例保留修改后的类型, 否则`T&`为。

## <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

using namespace std;
int main()
{
    int val = 0;
    add_lvalue_reference_t<int> p = (int&)val;
    p = p;  // to quiet "unused" warning
    cout << "add_lvalue_reference_t<int> == "
        << typeid(p).name() << endl;

    return (0);
}
```

```Output
add_lvalue_reference_t<int> == int
```

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[remove_reference 类](../standard-library/remove-reference-class.md)

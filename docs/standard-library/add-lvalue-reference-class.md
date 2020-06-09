---
title: add_lvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_lvalue_reference
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
ms.openlocfilehash: 5f822e3393853c780bfe4ee86d5a5c799ec7646d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617678"
---
# <a name="add_lvalue_reference-class"></a>add_lvalue_reference 类

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

如果*t*是左值引用，则类型修饰符的实例保留*修改后的*类型，否则为 `T&` 。

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

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](type-traits.md)\
[remove_reference 类](remove-reference-class.md)

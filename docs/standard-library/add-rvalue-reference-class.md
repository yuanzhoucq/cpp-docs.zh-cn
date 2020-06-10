---
title: add_rvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 6d7cc1d45ed3b963de0a0a004c1696ddbf0af440
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623918"
---
# <a name="add_rvalue_reference-class"></a>add_rvalue_reference 类

如果模板参数是对象或函数类型，则创建模板参数的右值引用类型。 否则，由于引用折叠的语义，类型与模板参数相同。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>参数

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

`add_rvalue_reference`类具有一个名为的成员 `type` ，该成员是模板参数*T*的右值引用类型的别名。引用折叠的语义意味着对于非对象类型和非函数类型*t*， `T&&` 为*t*。例如，当*T*是左值引用类型时， `add_rvalue_reference<T>::type` 是左值引用类型，而不是右值引用。

为方便起见， \<type_traits> 定义了一个用于 `add_rvalue_reference_t` 对的成员进行别名的帮助器模板 `type` `add_rvalue_reference` 。

## <a name="example"></a>示例

此代码示例使用 static_assert 来显示如何使用 `add_rvalue_reference` 和 `add_rvalue_reference_t` 创建右值引用类型，以及 `add_rvalue_reference` 针对左值引用类型的结果如何不是右值引用，而是到左值引用类型的折叠。

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>要求

标头：\<type_traits>

命名空间: std

## <a name="see-also"></a>另请参阅

[<type_traits>](type-traits.md)\
[add_lvalue_reference 类](add-lvalue-reference-class.md)\
[is_rvalue_reference 类](is-rvalue-reference-class.md)

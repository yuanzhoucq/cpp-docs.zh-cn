---
title: add_rvalue_reference 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: e5e658f16657c0021b78175e87d122a3accd11eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443651"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference 类

如果模板参数是对象或函数类型，则创建模板参数的右值引用类型。 否则，由于引用折叠的语义，类型与模板参数相同。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>参数

*T*<br/>
要修改的类型。

## <a name="remarks"></a>备注

`add_rvalue_reference`类具有一个名为成员`type`，即模板参数的右值引用的类型的别名*T*。引用折叠的语义意味着，对于非对象和非函数类型*T*，`T&&`是*T*。例如，当*T*是左值引用类型，`add_rvalue_reference<T>::type`为左值引用类型，不是右值引用。

为方便起见， \<type_traits > 定义帮助程序模板`add_rvalue_reference_t`，则该别名`type`的成员`add_rvalue_reference`。

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

标头： \<type_traits >

Namespace: std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference 类](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference 类](../standard-library/is-rvalue-reference-class.md)<br/>

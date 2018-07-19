---
title: add_lvalue_reference 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 710d7c154477320f7fb65f52f430f4c0666762c2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956942"
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

*T*要修改的类型。

## <a name="remarks"></a>备注

类型修饰符的实例保留修改的类型是*T*如果*T*是左值引用，否则`T&`。

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

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_reference 类](../standard-library/remove-reference-class.md)<br/>

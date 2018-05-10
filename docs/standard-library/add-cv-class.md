---
title: add_cv 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_cv
dev_langs:
- C++
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9825b690336acc8e93b0d404cc8335e5b27404b3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="addcv-class"></a>add_cv 类

从类型设置常量可变类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>参数

*T*要修改的类型。

## <a name="remarks"></a>备注

修改类型 `add_cv<T>` 的实例具有等同于由 [add_volatile](../standard-library/add-volatile-class.md) 和 [add_const](../standard-library/add-const-class.md) 修改的 *T* 的 `type` 成员 typedef，*T* 已经有 cv 限定符、是一个引用或者一个函数的情况除外。

`add_cv_t<T>` 帮组程序类型是访问 `add_cv<T>` 成员 typedef `type` 的快捷方式。

## <a name="example"></a>示例

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>要求

**标头：** \<type_traits > **Namespace:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const 类](../standard-library/remove-const-class.md)<br/>
[remove_volatile 类](../standard-library/remove-volatile-class.md)<br/>

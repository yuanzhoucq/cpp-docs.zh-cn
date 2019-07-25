---
title: add_cv 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 0cc63558ea392976bd6a3c5a43735c592e4606b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456598"
---
# <a name="addcv-class"></a>add_cv 类

从类型中进行**常量可变**类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>参数

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

修改后的类型`add_cv<T>`的实例具有与`type` [add_volatile](../standard-library/add-volatile-class.md)和[add_const](../standard-library/add-const-class.md)同时*修改的*等效的成员**typedef** , 除非已经有 cv 限定符, 是引用, 或者是才能.

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

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[remove_const 类](../standard-library/remove-const-class.md)\
[remove_volatile 类](../standard-library/remove-volatile-class.md)

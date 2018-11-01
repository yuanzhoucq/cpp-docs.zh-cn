---
title: mem_fun_t 类
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 32c66eb20215bc68efd0f0bb43c30f951da1bae9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456363"
---
# <a name="memfunt-class"></a>mem_fun_t 类

一种适配器类，允许`non_const`不采用任何参数，以使用指针自变量进行初始化的一元函数对象形式调用成员函数。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;

};
```

### <a name="parameters"></a>参数

*_Pm*<br/>
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*_Pleft*<br/>
该对象的 *_Pm*上调用成员函数。

## <a name="return-value"></a>返回值

一个自适应一元函数。

## <a name="remarks"></a>备注

此模板类存储一份 *_Pm*，它必须是指向类的成员函数的指针`Type`，私有成员对象中。 它将其成员函数 `operator()` 定义为返回 ( `_Pleft`->* `_Pm`)( )。

## <a name="example"></a>示例

通常不直接使用 `mem_fun_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<functional>](../standard-library/functional.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>

---
title: mem_fun1_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 42a6ee7c169d078e216b82365ab26d10838798c6
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006430"
---
# <a name="memfun1t-class"></a>mem_fun1_t 类

一种适配器类，允许`non_const`带一个自变量作为二元函数对象在使用指针自变量初始化时调用的成员函数。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

};
```

### <a name="parameters"></a>参数

*_Pm*<br/>
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*_Pleft*<br/>
该对象的 *_Pm*上调用成员函数。

*right*<br/>
为指定的参数 *_Pm*。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

此模板类存储一份 *_Pm*，它必须是指向类的成员函数的指针`Type`，私有成员对象中。 它定义其成员函数 `operator()` 为返回 ( **_Pleft**->\* `_Pm`)( **right**)。

## <a name="example"></a>示例

通常不直接使用 `mem_fun1_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>

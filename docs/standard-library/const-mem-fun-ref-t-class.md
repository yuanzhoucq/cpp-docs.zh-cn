---
title: const_mem_fun_ref_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 16025764cdcf28900c30ef53dced871998f8bd07
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006573"
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t 类

一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将不带任何自变量的 **const** 成员函数作为一元函数对象调用。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type>
class const_mem_fun_ref_t
: public unary_function<Type, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type& left) const;
};
```

### <a name="parameters"></a>参数

*Pm*<br/>
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*left*<br/>
该对象的*Pm*上调用成员函数。

## <a name="return-value"></a>返回值

一个自适应一元函数。

## <a name="remarks"></a>备注

此模板类存储一份*Pm*，它必须是指向类的成员函数的指针`Type`，私有成员对象中。 它定义其成员函数`operator()`为返回 (**左**。\*`Pm`) （) **const**。

## <a name="example"></a>示例

通常不直接使用 `const_mem_fun_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>

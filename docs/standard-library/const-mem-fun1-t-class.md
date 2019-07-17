---
title: const_mem_fun1_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 8ccd9d7e58b9cadec83b64df5553564db20a5745
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244519"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t 类

一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将仅带一个自变量的 **const** 成员函数作为二元函数对象调用。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>参数

*member_ptr*\
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*左侧*\
**Const**对象的*member_ptr*上调用成员函数。

*右侧*\
为指定的参数*member_ptr*。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

此模板类存储一份*member_ptr*，它必须是指向类的成员函数的指针`Type`，私有成员对象中。 它定义其成员函数`operator()`为返回`(left->member_ptr)(right) const`。

## <a name="example"></a>示例

很少直接使用 `const_mem_fun1_t` 的构造函数。 `mem_fn` 用于调整成员函数。 请参阅[mem_fn](../standard-library/functional-functions.md#mem_fn)有关如何使用成员函数适配器的示例。

---
title: const_mem_fun1_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 1af44635400037c6359b13c4f2925c3ac7f2d9d5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689754"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t 类

一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将仅带一个自变量的 **const** 成员函数作为二元函数对象调用。 在 c + + 11 中已弃用，在 c + + 17 中删除。

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

*member_ptr* \
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*左*\
在其上调用*member_ptr*成员函数的**const**对象。

*right* \
要提供给*member_ptr*的参数。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

类模板存储*member_ptr*的副本，该副本必须是指向私有成员对象中 `Type` 类的成员函数的指针。 它将其成员函数定义为返回 `(left->member_ptr)(right) const` `operator()`。

## <a name="example"></a>示例

很少直接使用 `const_mem_fun1_t` 的构造函数。 `mem_fn` 用于改编成员函数。 有关如何使用成员函数适配器的示例，请参阅[mem_fn](../standard-library/functional-functions.md#mem_fn) 。

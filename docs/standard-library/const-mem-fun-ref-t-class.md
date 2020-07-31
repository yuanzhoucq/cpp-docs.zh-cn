---
title: const_mem_fun_ref_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_ref_t
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
ms.openlocfilehash: 09d8569253dbeb1a873f4fc7b64b55658511d18e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228357"
---
# <a name="const_mem_fun_ref_t-class"></a>const_mem_fun_ref_t 类

一种适配器类， **`const`** 在使用引用自变量进行初始化时，该类允许将不带任何参数的成员函数作为一元函数对象调用。 在 c + + 11 中已弃用，在 c + + 17 中删除。

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

*下午*\
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*左中*\
在其上调用*Pm*成员函数的对象。

## <a name="return-value"></a>返回值

一个自适应一元函数。

## <a name="remarks"></a>备注

类模板*Pm* `Type` 在私有成员对象中存储 Pm 的副本，该副本必须是指向类的成员函数的指针。 它将其成员函数定义 `operator()` 为返回（**left** \* `Pm` ）。() **`const`**.

## <a name="example"></a>示例

通常不直接使用 `const_mem_fun_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。

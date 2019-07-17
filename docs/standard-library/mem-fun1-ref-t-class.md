---
title: mem_fun1_ref_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 88ab2c436b3dd3b5a289124e73b6f1b5d21f96a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243857"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t 类

一种适配器类，允许`non_const`带一个自变量作为二元函数对象在使用引用自变量初始化时调用的成员函数。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;
};
```

### <a name="parameters"></a>参数

*_Pm*\
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*左侧*\
该对象的 *_Pm*上调用成员函数。

*右侧*\
为指定的参数 *_Pm*。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

此模板类存储一份 *_Pm*，它必须是指向类的成员函数的指针`Type`，私有成员对象中。 它定义其成员函数`operator()`为返回 (**左**。\*`_Pm`) (**右**)。

## <a name="example"></a>示例

通常不直接使用 `mem_fun1_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。

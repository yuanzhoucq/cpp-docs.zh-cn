---
title: mem_fun1_ref_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 238d6147b2afa5ca3e143bc57aa4892e17d2c869
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687747"
---
# <a name="mem_fun1_ref_t-class"></a>mem_fun1_ref_t 类

一种适配器类，在使用引用自变量进行初始化时，它允许使用单个自变量的 `non_const` 成员函数作为二元函数对象调用。 在 c + + 11 中已弃用，在 c + + 17 中删除。

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

*_Pm* \
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*左*\
在其上调用 *_Pm*成员函数的对象。

*right* \
要提供给 *_Pm*的参数。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

类模板存储 *_Pm*的副本，该副本必须是指向私有成员对象中 `Type` 类的成员函数的指针。 它将其成员函数定义 `operator()` 为返回 **（\* `_Pm`）（** **右**）。

## <a name="example"></a>示例

通常不直接使用 `mem_fun1_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。

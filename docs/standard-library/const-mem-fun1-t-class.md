---
title: const_mem_fun1_t 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5fe5c06dd3017e867e73cf1107e619ec2c1edaf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843790"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t 类

一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将仅带一个自变量的 **const** 成员函数作为二元函数对象调用。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```

### <a name="parameters"></a>参数

`_Pm` 指向类成员函数的指针**类型**可转换为函数对象。

`_Pleft` **Const**对象`_Pm`上调用成员函数。

`right` 为指定的自变量`_Pm`。

## <a name="return-value"></a>返回值

一个自适应二元函数。

## <a name="remarks"></a>备注

模板类存储 `_Pm` 的副本，它必须是专用成员对象中指向类 **Type** 的成员函数的指针。 它定义其成员函数`operator()`为返回 ( **_Pleft** -> \* * Pm) (***右**) **const**。

## <a name="example"></a>示例

通常不直接使用 `const_mem_fun1_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>

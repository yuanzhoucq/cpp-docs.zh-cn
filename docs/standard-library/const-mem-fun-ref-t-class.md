---
title: const_mem_fun_ref_t 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun_ref_t class
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5051fe82a4d197a1518ccf9c0f3c797108c665e0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961244"
---
# <a name="constmemfunreft-class"></a>const_mem_fun_ref_t 类

一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将不带任何自变量的 **const** 成员函数作为一元函数对象调用。

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

*Pm*指向的类成员函数的指针`Type`可转换为函数对象。

*左*对象的*Pm*上调用成员函数。

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

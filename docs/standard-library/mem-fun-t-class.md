---
title: mem_fun_t 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xfunctional/std::mem_fun_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d49fbbcb921633df5231903085f094f8b9ec37e4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="memfunt-class"></a>mem_fun_t 类

一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将不带任何自变量的 **non_const** 成员函数作为一元函数对象调用。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;

};
```

### <a name="parameters"></a>参数

`_Pm` 指向类成员函数的指针**类型**可转换为函数对象。

`_Pleft` 对象的`_Pm`上调用成员函数。

## <a name="return-value"></a>返回值

一个自适应一元函数。

## <a name="remarks"></a>备注

模板类存储 `_Pm` 的副本，它必须是专用成员对象中指向类 **Type** 的成员函数的指针。 它将其成员函数 `operator()` 定义为返回 ( `_Pleft`->* `_Pm`)( )。

## <a name="example"></a>示例

通常不直接使用 `mem_fun_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<functional>](../standard-library/functional.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>

---
title: result_of 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95ac984ad164c242dcd470ed4d31f3921fa7ec56
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103261"
---
# <a name="resultof-class"></a>result_of 类

确定可调用类型的返回类型，该可调用类型采用指定参数类型。

## <a name="syntax"></a>语法

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>参数

*fn*<br/>
要查询的可调用类型。

*ArgTypes*<br/>
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板在编译时确定的结果类型`Fn`(`ArgTypes`)，其中*Fn*是可调用类型、 对函数引用或对中使用的类型的参数列表调用可调用类型的引用*ArgTypes*。 如果未计算的表达式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正确，则模板类的 `type` 成员为 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的结果类型命名。 否则，此模板类不具有任何成员 `type`。 类型*Fn*和参数包中的所有类型*ArgTypes*必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>

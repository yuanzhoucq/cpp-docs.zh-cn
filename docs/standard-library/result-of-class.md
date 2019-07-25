---
title: result_of 类
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 5a3265cfe4b2629bf02925ea6e3eeb0c4acb1e0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451215"
---
# <a name="resultof-class"></a>result_of 类

确定可调用类型的返回类型，该可调用类型采用指定参数类型。 在 c + + 14 中添加, 在 c + + 17 中已弃用。

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

*Fn*\
要查询的可调用类型。

*ArgTypes*\
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板可在编译时`Fn`确定 (`ArgTypes`) 的结果类型, 其中*Fn*是可调用类型、对函数的引用或对可调用类型的引用, 使用*ArgTypes*中的类型的自变量列表调用。 如果未计算的表达式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正确，则模板类的 `type` 成员为 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的结果类型命名。 否则，此模板类不具有任何成员 `type`。 类型*Fn*和参数包*ArgTypes*中的所有类型必须是完整的类型、 **void**或未知绑定的数组。 在 c + + 17 中弃用[invoke_result](invoke-result-class.md) 。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result 类](invoke-result-class.md)

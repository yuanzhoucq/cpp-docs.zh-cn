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
ms.openlocfilehash: f60a3ef6528da33fd1117fc940e961e9fe0987df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185901"
---
# <a name="resultof-class"></a>result_of 类

确定可调用类型的返回类型，该可调用类型采用指定参数类型。 添加在 C + + 14 中，在 C + + 17 中弃用。

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

使用此模板在编译时确定的结果类型`Fn`(`ArgTypes`)，其中*Fn*是可调用类型、 对函数引用或对中使用的类型的参数列表调用可调用类型的引用*ArgTypes*。 如果未计算的表达式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正确，则模板类的 `type` 成员为 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的结果类型命名。 否则，此模板类不具有任何成员 `type`。 类型*Fn*和参数包中的所有类型*ArgTypes*必须是完整类型**void**，或具有未知边界的数组。 不推荐使用的[invoke_result](invoke-result-class.md)在 C + + 17 中。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke_result 类](invoke-result-class.md)<br/>

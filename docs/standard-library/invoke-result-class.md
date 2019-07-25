---
title: invoke_result 类
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 2b2051b0c854151cff9b439f5ec0a951c25a6387
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447630"
---
# <a name="invokeresult-class"></a>invoke_result 类

确定在编译时采用指定参数类型的可调用类型的返回类型。 在 c + + 17 中添加。

## <a name="syntax"></a>语法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>参数

*多次*\
要查询的可调用类型。

*Args*\
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板可在编译时确定可*调用*(*args*...) 的结果类型, 其中, 可*调用*的和*参数*中的所有类型都是任何完整的类型、未知绑定的数组或可能的 cv `void`限定的。 模板类的 成员在使用arguments参数...调用时命名可调用的返回`type`类型。仅`type`当使用参数*Args*... 调用*时可以调用*可调用时, 才定义成员在未计算的上下文中。 否则, 该模板类不具有成员`type`, 这允许在编译时对特定参数类型集进行 SFINAE 测试。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)

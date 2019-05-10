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
ms.openlocfilehash: 7c03240d3ee666fcda30562279a8dbda2ca8dc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404840"
---
# <a name="invokeresult-class"></a>invoke_result 类

确定在编译时将指定的参数类型的可调用类型的返回类型。 添加 C + + 17 中。

## <a name="syntax"></a>语法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>参数

*Callable*<br/>
要查询的可调用类型。

*参数*<br/>
供可调用类型查询的参数列表的类型。

## <a name="remarks"></a>备注

使用此模板来确定的结果类型*Callable*(*Args*...) 在编译时，其中*Callable*和中的所有类型*Args*为任何完整类型、 未知边界的数组或可能限定了 cv `void`。 `type`的返回类型的模板类的成员名称*Callable*调用使用的参数时*Args*...`type`如果仅定义成员*Callable*时使用的自变量调用可调用*Args*...在未计算的上下文。 否则，此模板类具有任何成员`type`，它允许 SFINAE 对一组特定的参数类型在编译时测试。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)

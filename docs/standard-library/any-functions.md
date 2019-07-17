---
title: '&lt;任何&gt;函数'
ms.date: 04/04/2019
f1_keywords:
- any/std::any_cast
- any/std::make_any
- any/std::swap
ms.openlocfilehash: bb5f8b4411477cfcd33613ee0395227dced784f6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268739"
---
# <a name="ltanygt-functions"></a>&lt;任何&gt;函数

## <a name="any_cast"></a> any_cast

使变成了任何对象。

```cpp
template<class T>
    T any_cast(const any& operand);
template<class T>
    T any_cast(any& operand);
template<class T>
    T any_cast(any&& operand);
template<class T>
    const T* any_cast(const any* operand) noexcept;
template<class T>
    T* any_cast(any* operand) noexcept;
```

## <a name="make_any"></a> make_any

接受的值并创建的任何对象。

```cpp
template <class T, class... Args>
    any make_any(Args&& ...args);
template <class T, class U, class... Args>
    any make_any(initializer_list<U> il, Args&& ...args);
```

## <a name="swap"></a> 交换

任何交换两个对象的元素。

```cpp
void swap(any& left, any& right) noexcept;
```

### <a name="parameters"></a>参数

*左侧*\
一个 `any` 类型的对象。

*右侧*\
一个 `any` 类型的对象。

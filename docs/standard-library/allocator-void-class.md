---
title: allocator&lt;void&gt; 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: b6ca3f8b994756a21d85860fd8aff429ee38e58b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204925"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 类

类模板分配器到类型的专用化 **`void`** ，用于定义在此上下文中有意义的类型。

## <a name="syntax"></a>语法

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>备注

类为类型显式专用化类模板[分配](allocator-class.md)器 **`void`** 。 其构造函数和赋值运算符的行为与类模板的行为相同，但它只定义以下类型：

- [const_pointer](allocator-class.md#const_pointer)。

- [指针](allocator-class.md#pointer)。

- [value_type](allocator-class.md#value_type)。

- 重新[绑定](allocator-class.md#rebind)，嵌套类模板。

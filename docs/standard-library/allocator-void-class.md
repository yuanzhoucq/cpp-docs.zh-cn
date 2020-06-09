---
title: allocator&lt;void&gt; 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: af29c70dca56b1e68eef3614357269c587a77ec9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623682"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 类

类模板分配器到类型**void**的专用化，用于定义在此上下文中有意义的类型。

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

类显式专用化类型为**void**的类模板[分配](allocator-class.md)器。 其构造函数和赋值运算符的行为与类模板的行为相同，但它只定义以下类型：

- [const_pointer](allocator-class.md#const_pointer)。

- [指针](allocator-class.md#pointer)。

- [value_type](allocator-class.md#value_type)。

- 重新[绑定](allocator-class.md#rebind)，嵌套类模板。

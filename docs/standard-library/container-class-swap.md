---
title: Container Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: ccf4ae6ebc3ca13a42ca950310a60e30dbb27034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450775"
---
# <a name="container-classswap"></a>Container Class::swap

> [!NOTE]
> 本主题在 Microsoft C++文档中作为在C++标准库中使用的容器的非功能性示例。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

交换 **\*this** 和其参数之间的受控序列。

## <a name="syntax"></a>语法

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>备注

如果 **\*this.get\_ 分配器 ==** _right_ **.get_allocator**，它将在常量时间内执行交换。 否则，它所执行的元素分配和构造函数调用数量会与两个受控序列中的元素数量成正比。

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)

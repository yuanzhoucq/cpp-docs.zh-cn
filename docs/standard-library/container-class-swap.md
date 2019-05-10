---
title: Container Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: b344747c42e9b8b751b97747aacec0b39d10d6a1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221528"
---
# <a name="container-classswap"></a>Container Class::swap

> [!NOTE]
> 本主题是在 microsoftC++作为容器中使用的非功能性示例文档C++标准库。 有关详细信息，请参阅 [C++ 标准库容器](../standard-library/stl-containers.md)。

交换 **\*this** 和其参数之间的受控序列。

## <a name="syntax"></a>语法

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>备注

如果 **\*this.get\_ 分配器 ==** _right_ **.get_allocator**，它将在常量时间内执行交换。 否则，它所执行的元素分配和构造函数调用数量会与两个受控序列中的元素数量成正比。

## <a name="see-also"></a>请参阅

[Sample Container 类](../standard-library/sample-container-class.md)<br/>

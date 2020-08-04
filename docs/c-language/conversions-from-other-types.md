---
title: 从其他类型的转换
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: bd00bbb8944a0273163fa0c5952be510c9dd697c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200330"
---
# <a name="conversions-from-other-types"></a>从其他类型的转换

由于根据定义 `enum` 值是 `int` 值，因此与 `enum` 值之间的来回转换和 `int` 类型的转换是相同的。 对于 Microsoft C 编译器，整数与 `long` 相同。

**Microsoft 专用**

结构或联合类型之间不允许转换。

任何值都可以转换为类型 `void`，但此类转换的结果只能在放弃表达式值的上下文中（如在表达式语句中）使用。

根据定义，`void` 类型没有值。 因此，它不能转换为其他任何类型，而其他类型也不能通过赋值转换为 `void`。 不过，可以显式地将值强制转换为类型 `void`，如[类型强制转换](../c-language/type-cast-conversions.md)中所述。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[赋值转换](../c-language/assignment-conversions.md)

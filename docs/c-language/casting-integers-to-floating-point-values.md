---
title: 将整数转换为浮点值
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: b3c65beee0cef4eb74d1bad3c03e5a9c11efae27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227915"
---
# <a name="casting-integers-to-floating-point-values"></a>将整数转换为浮点值

**ANSI 3.2.1.3** 当一个整数转换为无法确切表示原始值的浮点数时的截断方向

当一个整数转换为无法确切表示值的浮点值时，值将被舍入（向上或向下）到最接近的适当值。

例如，将 `unsigned long`（精度为 32 位）强制转换为 `float`（尾数的精度为 23 位）会将数字舍入为 256 的最接近倍数。 介于 4,294,966,913 和 4,294,967,167 之间的所有 `long` 值都舍入为 `float` 值 4,294,967,040。

## <a name="see-also"></a>请参阅

[浮点数学](../c-language/floating-point-math.md)

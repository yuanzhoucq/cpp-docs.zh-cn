---
title: 将整数转换为浮点值
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: 8fa013668278fae82bcb2bb9eb1f2aec3cb61581
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152867"
---
# <a name="casting-integers-to-floating-point-values"></a>将整数转换为浮点值

**ANSI 3.2.1.3** 当一个整数转换为无法确切表示原始值的浮点数时的截断方向

当一个整数转换为无法确切表示值的浮点值时，值将被舍入（向上或向下）到最接近的适当值。

例如，将 unsigned long（具有 32 位精度）转换为 float（尾数具有 23 位精度）会将该数字舍入到 256 的最接近倍数。 介于 4,294,966,913 和 4,294,967,167 之间的所有 long 值都将舍入到 float 值 4,294,967,040。

## <a name="see-also"></a>请参阅

[浮点数学](../c-language/floating-point-math.md)

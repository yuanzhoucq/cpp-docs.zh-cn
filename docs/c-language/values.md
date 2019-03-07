---
title: 值
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: a745b9cc45ed3e58cab4ec7355707d93a0557c04
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150033"
---
# <a name="values"></a>值

**ANSI 3.1.2.5** 各种类型的浮点数的表示形式和值集

float 类型包含 32 位：1 位用于符号，8 位用于指数，23 位用于尾数。 其范围为精度至少为 7 个数字的 +/- 3.4E38。

double 类型包含 64 位：1 位用于符号，11 位用于指数，52 位用于尾数。 其范围为精度至少为 15 个数字的 +/- 1.7E308。

long double 类型包含 80 位：1 位用于符号，15 位用于指数，64 位用于尾数。 其范围为精度至少为 19 个数字的 +/- 1.2E4932。 请注意，利用 Microsoft C 编译器，**long double** 类型的表示形式与 **double** 类型的表示形式相同。

## <a name="see-also"></a>请参阅

[浮点数学](../c-language/floating-point-math.md)

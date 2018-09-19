---
title: 值 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bef044535d2f5a5b337823b1798feaea48745d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106268"
---
# <a name="values"></a>值

**ANSI 3.1.2.5** 各种类型的浮点数的表示形式和值集

**float** 类型包含 32 位：1 表示符号，8 表示指数，23 表示尾数。 其范围为精度至少为 7 个数字的 +/- 3.4E38。

**double** 类型包含 64 位：1 表示符号，11 表示指数，52 表示尾数。 其范围为精度至少为 15 个数字的 +/- 1.7E308。

**long double** 类型包含 80 位：1 表示符号，15 表示指数，64 表示尾数。 其范围为精度至少为 19 个数字的 +/- 1.2E4932。 请注意，利用 Microsoft C 编译器，**long double** 类型的表示形式与 **double** 类型的表示形式相同。

## <a name="see-also"></a>请参阅

[浮点数学](../c-language/floating-point-math.md)
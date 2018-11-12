---
title: 整数的降级
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: 5dca8d414e7cf7dd04d405208ad6a86dd4372542
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480896"
---
# <a name="demotion-of-integers"></a>整数的降级

**ANSI 3.2.1.2**：在值无法表示的情况下，将整数转换为较短的带符号整数的结果，或者将无符号整数转换为同等长度的带符号整数的结果

当 **long** 整数强制转换为 **short** 时，或者 **short** 转换为 `char` 时，将保留最低有效字节。

例如，此行

```
short x = (short)0x12345678L;
```

将值 0x5678 赋给 `x`，此行

```
char y = (char)0x1234;
```

将值 0x34 赋给 `y`。

当带符号变量转换无符号变量（或相反）时，位模式保持不变。 例如，将 -2 (0xFE) 强制转换为无符号值将生成 254（也是 0xFE）。

## <a name="see-also"></a>请参阅

[整数](../c-language/integers.md)
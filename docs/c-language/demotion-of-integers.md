---
title: 整数的降级
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: aee0a5041cd37b1fbad785b760b8cefde74eb195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218879"
---
# <a name="demotion-of-integers"></a>整数的降级

**ANSI 3.2.1.2**：在值无法表示的情况下，将整数转换为较短的带符号整数的结果，或者将无符号整数转换为同等长度的带符号整数的结果

如果 `long` 整数被强制转换为 `short`，或 `short` 被强制转换为 `char`，则保留最低有效字节。

例如，此行

```
short x = (short)0x12345678L;
```

将值 0x5678 赋给 `x`，此行

```
char y = (char)0x1234;
```

将值 0x34 赋给 `y`。

如果 `signed` 变量转换为 `unsigned` 变量（反之亦然），位模式保持不变。 例如，将 -2 (0xFE) 强制转换为 `unsigned` 值将得到 254（也是 0xFE）。

## <a name="see-also"></a>请参阅

[整数](../c-language/integers.md)

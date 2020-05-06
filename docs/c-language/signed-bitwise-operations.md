---
title: 带符号的按位运算
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158312"
---
# <a name="signed-bitwise-operations"></a>带符号的按位运算

**ANSI 3.3**：对带符号整数进行的按位运算的结果

对带符号整数进行的按位运算的工作方式与对无符号整数进行的按位运算的工作方式相同。 例如，`-16 & 99` 可用二进制格式表示

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

按位“与”的结果为 96。

## <a name="see-also"></a>请参阅

[整数](../c-language/integers.md)

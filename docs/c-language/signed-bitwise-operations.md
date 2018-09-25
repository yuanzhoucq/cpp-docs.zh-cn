---
title: 带符号的按位运算 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184fd5a0e6c12cb58e9fed759459e7b8172896f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038290"
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
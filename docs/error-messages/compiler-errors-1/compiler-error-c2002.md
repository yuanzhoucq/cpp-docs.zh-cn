---
title: 编译器错误 C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442843"
---
# <a name="compiler-error-c2002"></a>编译器错误 C2002

无效的宽字符常量

多字节字符常量无效。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 宽字符常量包含比预期更多的字节。

1. 不包括标准标头 STDDEF.h。

1. 不能使用常规字符串文本串联宽字符。

1. 宽字符常量前面必须是字符 L:

    ```
    L'mbconst'
    ```

1. Microsoft c + + 预处理器指令的文本参数必须为 ASCII。 例如，指令`#pragma message(L"string")`，不是有效。
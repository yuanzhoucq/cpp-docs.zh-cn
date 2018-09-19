---
title: 编译器错误 C2002 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87a7fe1513c695344676624ae1968060097c885
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116914"
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
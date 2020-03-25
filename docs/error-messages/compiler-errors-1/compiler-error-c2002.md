---
title: 编译器错误 C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208242"
---
# <a name="compiler-error-c2002"></a>编译器错误 C2002

宽字符常量无效

多字节字符常量无效。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 宽字符常数包含比预期更多的字节。

1. 标准标头 STDDEF.H 不包括在内。

1. 宽字符不能与普通字符串连接。

1. 宽字符常量前面必须是字符 "L"：

    ```
    L'mbconst'
    ```

1. 对于 Microsoft C++，预处理器指令的文本参数必须为 ASCII。 例如，指令 `#pragma message(L"string")`无效。

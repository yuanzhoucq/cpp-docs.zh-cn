---
title: 编译器错误 C3872 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3872
dev_langs:
- C++
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec6450dca0faa86f3cf27452eff6df9851742d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018829"
---
# <a name="compiler-error-c3872"></a>编译器错误 C3872

“char”：此字符不允许在标识符中使用

C++ 编译器对于标识符中允许的字符遵循 C++ 11 标准。 仅允许在标识符中使用某些范围的字符和通用字符名称。 其他限制适用于标识符的初始字符。 有关允许的字符和通用字符名称范围的详细信息和列表，请参阅 [Identifiers](../../cpp/identifiers-cpp.md)。

编译 C++/CLI 代码时，标识符中允许的字符范围限制更少。 使用 /clr 编译的代码中的标识符应遵循  [标准 ECMA-335：公共语言基础结构 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。

下面的示例生成 C3872：

```
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```
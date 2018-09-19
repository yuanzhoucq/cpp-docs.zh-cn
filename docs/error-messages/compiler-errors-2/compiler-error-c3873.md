---
title: 编译器错误 C3873 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83580d8202dada0b650b1703dcadf9b99e6771d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072805"
---
# <a name="compiler-error-c3873"></a>编译器错误 C3873

“char”：不允许将此字符作为标识符的第一个字符

C++ 编译器对于标识符中允许的字符遵循 C++ 11 标准。 仅允许在标识符中使用某些范围的字符和通用字符名称。 其他限制适用于标识符的初始字符。 有关允许的字符和通用字符名称范围的详细信息和列表，请参阅 [Identifiers](../../cpp/identifiers-cpp.md)。

编译 C++/CLI 代码时，标识符中允许的字符范围限制更少。 使用 /clr 编译的代码中的标识符应遵循  [标准 ECMA-335：公共语言基础结构 (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。

下面的示例生成 C3873：

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```
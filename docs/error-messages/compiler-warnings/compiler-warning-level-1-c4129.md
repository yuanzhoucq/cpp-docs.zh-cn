---
title: 编译器警告（等级1） C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: ab3108c60c18276e8e4797c7cfde1b66535dbaaa
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627418"
---
# <a name="compiler-warning-level-1-c4129"></a>编译器警告（等级1） C4129

"character"：无法识别的字符转义序列

字符或字符串常量中反斜杠（\\）后面的 `character` 未被识别为有效的转义序列。 反斜杠将被忽略且不打印。 打印反斜杠后的字符。

若要打印单个反斜杠，请指定双反斜杠（\\\\）。

2\.13.2 C++部分中的标准讨论了转义序列。

下面的示例生成 C4129：

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
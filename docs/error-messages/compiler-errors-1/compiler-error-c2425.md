---
title: 编译器错误 C2425
ms.date: 11/04/2016
f1_keywords:
- C2425
helpviewer_keywords:
- C2425
ms.assetid: 0ce59404-9aff-4e01-aa8d-27d23e92eb30
ms.openlocfilehash: fcbcf06df3330320bf014c132abc543e2e2e8087
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479011"
---
# <a name="compiler-error-c2425"></a>编译器错误 C2425

“令牌”：“上下文”中的非常量表达式

此令牌构成此上下文中非常量表达式的一部分。

若要解决此问题，请用常量文本或计算替换此令牌。

以下示例生成 C2425：

```
// C2425.cpp
// processor: x86
int main() {
   int i = 3;
   __asm {
      mov eax, [ebp - i]   // C2425
      mov eax, [ebp - 3]   // OK
   }
}
```
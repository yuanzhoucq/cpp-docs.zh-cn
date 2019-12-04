---
title: 编译器错误 C2431
ms.date: 11/04/2016
f1_keywords:
- C2431
helpviewer_keywords:
- C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
ms.openlocfilehash: 135f73490cf23313d4ac4e2a5f568f2b6100422b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744519"
---
# <a name="compiler-error-c2431"></a>编译器错误 C2431

"identifier" 中的索引寄存器非法

ESP 寄存器缩放或用作索引和基寄存器。 X86 处理器的 SIB 编码不允许这两种方法。

下面的示例生成 C2431：

```cpp
// C2431.cpp
// processor: x86
int main() {
   _asm mov ax, [ESI + 2*ESP]   // C2431
   _asm mov ax, [esp + esp]   // C2431
}
```

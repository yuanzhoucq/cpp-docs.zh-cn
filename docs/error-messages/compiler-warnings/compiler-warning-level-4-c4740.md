---
title: 编译器警告（等级 4）C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 936dfb5464eabe7b1ac44df24445224fb9e204a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457878"
---
# <a name="compiler-warning-level-4-c4740"></a>编译器警告（等级 4）C4740

工作流中或出内联 asm 代码会取消全局优化

当在跳转或向外`asm`块中，该函数禁用全局优化。

下面的示例生成 C4740:

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```
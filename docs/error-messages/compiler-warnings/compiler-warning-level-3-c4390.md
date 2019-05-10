---
title: 编译器警告（等级 3）C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 4ca00f892adc8fe3ac1bffb59a27ea1744249dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401977"
---
# <a name="compiler-warning-level-3-c4390"></a>编译器警告（等级 3）C4390

';': 找到空的受控的语句;这是目的？

不包含指令的控制语句后找到一个分号。

如果您收到 C4390 宏，则应使用[警告](../../preprocessor/warning.md)杂注来禁用 C4390 中包含宏的模块。

下面的示例生成 C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
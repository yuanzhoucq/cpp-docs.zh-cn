---
title: 编译器警告 （等级 1） C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 40c6724daf17c1c0b546bb7bc64bb704f732e8d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441244"
---
# <a name="compiler-warning-level-1-c4010"></a>编译器警告 （等级 1） C4010

单行注释包含行继续符

单行注释，引入的 / / 包含反斜杠 (\\) 用作行继续符。 编译器会考虑延续的下一行，并将其视为一条注释。

某些语法导向型编辑器并不表示在后是继续符为注释的行。 忽略语法突出显示的任何行的会导致此警告。

下面的示例生成 C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
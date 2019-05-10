---
title: 编译器警告（等级 1）C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: 1fb2dc7fd4bc685e457898b47c513c21009146ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410351"
---
# <a name="compiler-warning-level-1-c4552"></a>编译器警告（等级 1）C4552

operator： 运算符不起任何作用;应输入带副作用的运算符

如果表达式语句作为表达式的顶部具有一个没有任何副作用的运算符，它可能是一个错误。

若要覆盖此警告，请将表达式放在括号中。

下面的示例生成 C4552:

```
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```
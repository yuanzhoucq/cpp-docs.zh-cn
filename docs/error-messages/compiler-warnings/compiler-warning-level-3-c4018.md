---
title: 编译器警告 （等级 3） C4018
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: 6436f62a06cbe931ca5b42751d60507f21675c5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402367"
---
# <a name="compiler-warning-level-3-c4018"></a>编译器警告 （等级 3） C4018

expression： 有符号/无符号不匹配

比较符号和无符号数字所需的编译器将有符号的值转换为无符号。

如果要转换的两种类型一个测试签名和未签名的类型时，可能会修复此警告。

下面的示例生成 C4018:

```
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```
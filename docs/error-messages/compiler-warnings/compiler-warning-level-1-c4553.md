---
title: 编译器警告 （等级 1） C4553 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4553
dev_langs:
- C++
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17c5887b550ea3181ac51d23ee24928502da1003
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096426"
---
# <a name="compiler-warning-level-1-c4553"></a>编译器警告（等级 1）C4553

operator： 运算符不起任何作用;是否要使用 operator？

如果表达式语句作为表达式的顶部具有一个没有任何副作用的运算符，它可能是一个错误。

下面的示例生成 C4553:

```
// C4553.cpp
// compile with: /W1
int func()
{
   return 0;
}

int main()
{
   int i;
   i == func();   // C4553
   // try the following line instead
   // i = func();
}
```
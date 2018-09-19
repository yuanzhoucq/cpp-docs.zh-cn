---
title: 编译器警告 （等级 1） C4552 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4552
dev_langs:
- C++
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62c08ea81f5f8794a1dd4ff7d0b5644e9a669e0f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048066"
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
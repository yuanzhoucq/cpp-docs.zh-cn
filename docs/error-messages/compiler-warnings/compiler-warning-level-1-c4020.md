---
title: 编译器警告 （等级 1） C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 75148c210ddd2a611061d58c036d12c084f442cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482021"
---
# <a name="compiler-warning-level-1-c4020"></a>编译器警告 （等级 1） C4020

function： 实参太多

函数调用中的实际参数的数目超出了函数原型或定义中的正式参数的数目。 编译器将根据该函数的调用约定的额外实际参数传递。

下面的示例生成 C4020:

```
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

可能的解决方法：

```
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```
---
title: 编译器错误 C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 8350c5baf129b88c178be280d2da7fe856c6cf57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517606"
---
# <a name="compiler-error-c2561"></a>编译器错误 C2561

identifier： 函数必须返回值

该函数被声明为返回一个值，但函数定义不包含`return`语句。

此错误可能引起错误的函数原型：

1. 如果该函数不返回一个值，声明该函数返回类型与[void](../../cpp/void-cpp.md)。

1. 检查所有的可能分支，该函数的返回类型在原型中声明的值。

1. C + + 函数包含存储中的返回值的内联程序集例程`AX`注册可能需要的 return 语句。 中的值复制`AX`给临时变量，并从该函数返回该变量。

下面的示例生成 C2561:

```
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
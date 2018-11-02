---
title: 编译器警告（等级 1）C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: bcadf31eda079ebb8ea7a496efe4c945e16b1ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622834"
---
# <a name="compiler-warning-level-1-c4532"></a>编译器警告（等级 1）C4532

continue: __finally/finally 块中的跳转具有未定义的行为在终止处理期间

编译器遇到以下关键字之一：

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

导致带跳转[__finally](../../cpp/try-finally-statement.md)或[最后](../../dotnet/finally.md)异常终止期间的块。

如果发生异常，并在终止处理程序执行过程正在展开堆栈时 (`__finally`块或 finally 块)，和你的代码跳出`__finally`之前阻止`__finally`块结束，行为是不确定。 控件可能不返回到展开的代码，以便不会正确处理异常。

如果您必须共跳转 **__finally**块中，首先检查异常终止。

下面的示例生成 C4532;只需注释掉跳转语句，若要解决此警告。

```
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```
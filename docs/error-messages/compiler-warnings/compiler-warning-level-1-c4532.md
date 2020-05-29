---
title: 编译器警告（等级 1）C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: 97ef7093aa56b41b869979e09d77fc448c6cf43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186434"
---
# <a name="compiler-warning-level-1-c4532"></a>编译器警告（等级 1）C4532

"continue"：在终止处理期间跳出 __finally/finally 块具有未定义的行为

编译器遇到以下关键字之一：

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

导致在异常终止期间跳出[__finally](../../cpp/try-finally-statement.md)或[finally](../../dotnet/finally.md)块。

如果发生了异常，并且在终止处理程序（`__finally` 或 finally 块）的执行期间展开堆栈，并且代码在 `__finally` 块结束之前跳出 `__finally` 块，则该行为是不确定的。 控件不能返回到展开代码，因此异常可能不会得到正确处理。

如果必须跳出 **__finally**块，请首先检查异常终止。

下面的示例生成 C4532;只需注释掉跳转语句即可解决警告。

```cpp
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

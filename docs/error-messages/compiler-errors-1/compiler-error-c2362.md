---
title: 编译器错误 C2362
ms.date: 11/04/2016
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 17656b2a48a3680a9269d3ca300fd4188eda6b84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661105"
---
# <a name="compiler-error-c2362"></a>编译器错误 C2362

goto label 跳过 identifier 的初始化

使用编译时[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳转到标签会无法标识符初始化。

除非声明将封闭的块不输入中不能跳过具有初始值设定项的声明或变量已初始化。

下面的示例生成 C2326:

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

可能的解决方法：

```
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```
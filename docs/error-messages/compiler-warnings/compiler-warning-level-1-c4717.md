---
title: 编译器警告（等级 1）C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0cf9aef8f68ca5972fd3d7886cd8061b88d043ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442557"
---
# <a name="compiler-warning-level-1-c4717"></a>编译器警告（等级 1）C4717

function： 递归的所有控件路径，函数将导致运行时堆栈溢出

通过函数的每个路径包含对该函数的调用。 由于没有办法退出而无需本身的第一个调用函数以递归方式，将永远不会退出该函数。

下面的示例生成 C4717:

```
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```
---
title: 编译器警告（等级1） C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0bc95cc770914a1c02a7a40f9754415c2f013d63
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051349"
---
# <a name="compiler-warning-level-1-c4717"></a>编译器警告（等级1） C4717

"function"：递归所有控件路径，函数将导致运行时堆栈溢出

通过函数的每个路径都包含对函数的调用。 由于无法先以递归方式自行调用函数而退出函数，因此该函数将永远不会退出。

下面的示例生成 C4717：

```cpp
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
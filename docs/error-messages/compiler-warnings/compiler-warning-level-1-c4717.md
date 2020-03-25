---
title: 编译器警告（等级 1）C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 40897e54601793431671bc14f855db43e905c656
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175283"
---
# <a name="compiler-warning-level-1-c4717"></a>编译器警告（等级 1）C4717

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

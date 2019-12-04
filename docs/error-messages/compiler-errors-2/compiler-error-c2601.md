---
title: 编译器错误 C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 87b5afe2133bb737a8f9c855b0652c2f50ca27ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740515"
---
# <a name="compiler-error-c2601"></a>编译器错误 C2601

"function"：本地函数定义是非法的

代码尝试在函数内定义函数。

或者，在 C2601 错误位置之前，你的源代码中可能有一个额外的大括号。

下面的示例生成 C2601：

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```

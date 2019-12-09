---
title: 编译器错误 C2824
ms.date: 11/04/2016
f1_keywords:
- C2824
helpviewer_keywords:
- C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
ms.openlocfilehash: ee012d7244079fd881210eb969f4844a2c6e85d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750632"
---
# <a name="compiler-error-c2824"></a>编译器错误 C2824

"operator new" 的返回类型必须为 "void *"

对于非基于的指针，运算符 `new` 的重载必须返回 `void *`。

下面的示例生成 C2824：

```cpp
// C2824.cpp
// compile with: /c
class   A {
   A* operator new(size_t i, char *m);   // C2824
   // try the following line instead
   // void* operator new(size_t i, char *m);
};
```

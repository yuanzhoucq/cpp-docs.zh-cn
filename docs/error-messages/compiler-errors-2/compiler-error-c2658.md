---
title: 编译器错误 C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 77a9122d20561ceee4f211394b3b81900d5580ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756079"
---
# <a name="compiler-error-c2658"></a>编译器错误 C2658

"member"：匿名结构/联合中的重定义

两个匿名结构或联合包含具有相同标识符但类型不同的成员声明。 在[/za](../../build/reference/za-ze-disable-language-extensions.md)下，对于具有相同标识符和类型的成员，也会出现此错误。

下面的示例生成 C2658：

```cpp
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```

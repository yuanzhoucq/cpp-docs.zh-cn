---
title: 编译器错误 C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: 5743aba880f23d7706940936fc4a3a1973a84ca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558244"
---
# <a name="compiler-error-c2032"></a>编译器错误 C2032

identifier： 函数不能是成员的结构/联合 structorunion

结构或联合有一个 c + + 中，但不是在 C 中允许的成员函数若要解决此错误，请编译为 c + + 程序或删除成员函数。

下面的示例生成 C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

可能的解决方法：

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
---
title: 编译器错误 C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 414b6e53cf1610a55db984a1127bfc884102494f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589585"
---
# <a name="compiler-error-c2460"></a>编译器错误 C2460

identifier1： 使用 identifier2，正在定义的

类或结构 (`identifier2`) 声明为其自身的成员 (`identifier1`)。 不允许递归定义的类和结构。

下面的示例生成 C2460:

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

相反，在类中使用的指针引用。

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```
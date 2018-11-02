---
title: 编译器错误 C2133
ms.date: 11/04/2016
f1_keywords:
- C2133
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
ms.openlocfilehash: 68672ae76024d3d09d738d997c485a3205c7dd2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588053"
---
# <a name="compiler-error-c2133"></a>编译器错误 C2133

identifier： 未知的大小

未确定大小的数组声明为类、 结构、 联合或枚举的成员。 /Za (ANSI C) 选项不允许未确定大小的成员数组。

下面的示例生成 C2133:

```
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

可能的解决方法：

```
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```
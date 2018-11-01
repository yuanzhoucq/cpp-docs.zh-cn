---
title: 编译器错误 C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 873ab4d4b016fa392b7a2f64fdd14c3e93f2e22d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516085"
---
# <a name="compiler-error-c3283"></a>编译器错误 C3283

“类型”: 接口不能包含实例构造函数

CLR [接口](../../windows/interface-class-cpp-component-extensions.md) 不能包含实例构造函数。  允许使用静态构造函数。

以下示例生成 C3283:

```
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

可能的解决方法：

```
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```
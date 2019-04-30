---
title: 编译器错误 C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 593b04b8593e261aa1980ada7693300b52a869c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381574"
---
# <a name="compiler-error-c3283"></a>编译器错误 C3283

“类型”: 接口不能包含实例构造函数

CLR [接口](../../extensions/interface-class-cpp-component-extensions.md) 不能包含实例构造函数。  允许使用静态构造函数。

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
---
title: 编译器错误 C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: e41ea1dbe1f2bd47f9b557d502ec95bcecb1e2a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428258"
---
# <a name="compiler-error-c3887"></a>编译器错误 C3887

var: literal 数据成员的初始值设定项必须是常量表达式

一个[文字](../../windows/literal-cpp-component-extensions.md)只能使用常量表达式进行初始化数据成员。

下面的示例生成 C3887:

```
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

可能的解决方法：

```
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```
---
title: 编译器错误 C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303510"
---
# <a name="compiler-error-c2396"></a>编译器错误 C2396

your_type:: operator'type ':CLR 或 WinRT 用户定义的转换 functionnot 有效。 必须从转换或转换为：' T ^，' T ^ %'，' T ^ &，其中 T = your_type

Windows 运行时或托管类型中的转换函数没有至少一个类型与包含转换函数的类型相同的参数。

下面的示例生成 C2396，并演示如何修复此错误：

```
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```
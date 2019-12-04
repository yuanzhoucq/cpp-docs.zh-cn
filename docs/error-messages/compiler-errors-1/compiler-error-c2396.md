---
title: 编译器错误 C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744831"
---
# <a name="compiler-error-c2396"></a>编译器错误 C2396

"your_type：： operator'type" "： CLR 或 WinRT 用户定义的转换 functionnot 有效。 必须转换为： t ^ "，不是 ^%"，不是 ^ & "，其中 T =" your_type "

Windows 运行时或托管类型中的转换函数没有至少一个类型与包含转换函数的类型相同的参数。

下面的示例生成 C2396，并演示如何修复此错误：

```cpp
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

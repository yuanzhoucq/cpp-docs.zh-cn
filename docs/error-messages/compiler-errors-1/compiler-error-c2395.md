---
title: 编译器错误 C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: 2ac59856770b04dd3c4ea14360e0a83dd99f2150
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744935"
---
# <a name="compiler-error-c2395"></a>编译器错误 C2395

“your_type::operator'op'”：CLR 或 WinRT 运算符无效。 至少一个参数必须是以下类型： "t"、"t%"、"& t"、"t ^"、"t ^%"、"t ^ &"，其中 T = "your_type"

Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。

下面的示例生成 C2395，并演示如何修复此错误：

```cpp
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```

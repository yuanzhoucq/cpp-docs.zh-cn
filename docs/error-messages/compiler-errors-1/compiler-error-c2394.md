---
title: 编译器错误 C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: 2c8c23939298f5603b59636ede08b65acaa0f22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744987"
---
# <a name="compiler-error-c2394"></a>编译器错误 C2394

"your_type：： operator'op" "： CLR 或 WinRToperator 无效。 至少一个参数必须是以下类型： "t ^"、"t ^%"、"t ^ &"，其中 T = "your_type"

Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。

以下示例生成 C2394：

```cpp
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```

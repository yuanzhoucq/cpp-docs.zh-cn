---
title: 编译器错误 C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: a18b09bcb5e6f4e743a8b1668cd0057b02a60a8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303692"
---
# <a name="compiler-error-c2394"></a>编译器错误 C2394

your_type:: operator'op'":CLR 或 WinRToperator 无效。 至少一个参数必须是以下类型之一：' T ^，' T ^ %'，' T ^ &，其中 T = your_type

Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。

以下示例生成 C2394：

```
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
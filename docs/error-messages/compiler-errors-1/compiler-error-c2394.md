---
title: 编译器错误 C2394 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2394
dev_langs:
- C++
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfb1db7ab7cb1b44ff61d4cf6d5a22d5365da4b4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051680"
---
# <a name="compiler-error-c2394"></a>编译器错误 C2394

your_type:: operator'op'": CLR 或 WinRToperator 无效。 至少一个参数必须是以下类型：“T^”、“T^%”、“T^&”，其中 T =“your_type”

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
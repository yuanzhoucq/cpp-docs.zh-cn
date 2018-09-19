---
title: 编译器错误 C2395 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99d9a1be42a36baac2037e4289cb24db2f45b563
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050536"
---
# <a name="compiler-error-c2395"></a>编译器错误 C2395

“your_type::operator'op'”：CLR 或 WinRT 运算符无效。 至少一个参数必须是以下类型：“T”、“T%”、“T&”、“T^”、“T^%”、“T^&”，其中 T =“your_type”

Windows 运行时或托管的类型中的一个运算符没有至少一个类型与运算符返回值的类型相同的参数。

下面的示例生成 C2395，并演示如何修复此错误：

```
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
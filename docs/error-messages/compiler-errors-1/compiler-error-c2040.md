---
title: 编译器错误 C2040 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccfbacff97550e20c0dd0202e0737585ffd39d6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016463"
---
# <a name="compiler-error-c2040"></a>编译器错误 C2040

“运算符”:“identifier1”与“identifier2”的间接级别不同

涉及指定操作数的表达式具有不兼容的操作数类型或隐式转换的操作数类型。 如果这两个操作数都是算术的，或两个都是非算术的（如数组或指针），使用时将不做更改。 如果一个操作数是算术的而另一个不是算术的，则算术操作数将转换为非算术操作数的类型。

此示例生成 C2040，并演示如何对其进行修复。

```
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```
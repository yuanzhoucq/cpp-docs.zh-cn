---
title: 编译器错误 C2805 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2805
dev_langs:
- C++
helpviewer_keywords:
- C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad07ea30d4124c0655e739e0e9222b3dc428a0a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032232"
---
# <a name="compiler-error-c2805"></a>编译器错误 C2805

二进制 operator operator 具有参数太少

二元运算符没有任何参数。

下面的示例生成 C2805:

```
// C2805.cpp
// compile with: /c
class X {
public:
   X operator< ( void );   // C2805 must take one parameter
   X operator< ( X );   // OK
};
```
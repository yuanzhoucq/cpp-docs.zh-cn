---
title: 编译器错误 C2806 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2806
dev_langs:
- C++
helpviewer_keywords:
- C2806
ms.assetid: 7c9ff1f4-1590-4c47-991d-b1075a173b48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01cf48170c8fc8b73f9c4cbe36c051a8daff4314
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043633"
---
# <a name="compiler-error-c2806"></a>编译器错误 C2806

operator operator 具有形参太多

重载的运算符具有太多参数。

下面的示例生成 C2806:

```
// C2806.cpp
// compile with: /c
class X {
public:
   X operator++ ( int, int );   // C2806 more than 1 parameter
   X operator++ ( int );   // OK
} ;
```
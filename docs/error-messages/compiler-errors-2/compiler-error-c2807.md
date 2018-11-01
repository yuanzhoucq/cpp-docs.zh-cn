---
title: 编译器错误 C2807
ms.date: 11/04/2016
f1_keywords:
- C2807
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
ms.openlocfilehash: 5e3fd05b1c2473efbc1cd102056c73b2f221981d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527928"
---
# <a name="compiler-error-c2807"></a>编译器错误 C2807

第二个形参以后缀 operator operator 必须为 int

后缀运算符的第二个参数具有错误的类型。

下面的示例生成 C2807:

```
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```
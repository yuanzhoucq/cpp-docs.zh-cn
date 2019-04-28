---
title: 编译器错误 C2809
ms.date: 11/04/2016
f1_keywords:
- C2809
helpviewer_keywords:
- C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
ms.openlocfilehash: d9dffabf318d51a97c172ecee2e4b2d4183a81f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281893"
---
# <a name="compiler-error-c2809"></a>编译器错误 C2809

operator operator 具有没有形参

运算符缺少必需的参数。

下面的示例生成 C2809:

```
// C2809.cpp
// compile with: /c
class A{};
int operator+ ();   // C2809
int operator+ (A);   // OK
```
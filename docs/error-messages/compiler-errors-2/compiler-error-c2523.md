---
title: 编译器错误 C2523
ms.date: 11/04/2016
f1_keywords:
- C2523
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
ms.openlocfilehash: 88a55a469fb8bc08d2ae73209c2e98a99dbc1df0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482012"
---
# <a name="compiler-error-c2523"></a>编译器错误 C2523

类:: ~ 标识符： 析构函数/终结器标记不匹配

析构函数的名称必须是类名前面是波形符 (`~`)。 构造函数和析构函数具有与类相同的名称的唯一成员。

下面的示例生成 C2523:

```
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```
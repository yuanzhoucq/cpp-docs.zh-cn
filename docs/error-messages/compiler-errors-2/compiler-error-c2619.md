---
title: 编译器错误 C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: f82b315a3e7ae4bb1f6d281e1d80ddc2c7fb0dea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662904"
---
# <a name="compiler-error-c2619"></a>编译器错误 C2619

“标识符”：匿名结构或联合中不允许使用静态数据成员

匿名结构或联合的成员声明为 `static`。

下面的示例生成 C2619，并演示如何通过删除 static 关键字修复此错误。

```
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```
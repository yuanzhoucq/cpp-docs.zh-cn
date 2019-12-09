---
title: 编译器错误 C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: 3ca5ea4612091f1e3eee8fead2b1eaebb264b696
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754766"
---
# <a name="compiler-error-c2619"></a>编译器错误 C2619

“标识符”：匿名结构或联合中不允许使用静态数据成员

匿名结构或联合的成员声明为 `static`。

下面的示例生成 C2619，并演示如何通过删除 static 关键字修复此错误。

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```

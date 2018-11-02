---
title: 编译器警告（等级 1） C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: b6fc5708d4e2f9982ceaab57260f13e134e4d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578251"
---
# <a name="compiler-warning-level-1-c4806"></a>编译器警告（等级 1） C4806

“operation”：不安全的操作：提升到类型 “type” 的类型 “type” 没有值与给定的常量相等

此消息警告针对代码如 `b == 3`，其中 `b` 具有类型 `bool`。 提升规则使 `bool` 被提升为 `int`。 这是合法的但绝不为 **真**。 以下示例生成 C4806：

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```
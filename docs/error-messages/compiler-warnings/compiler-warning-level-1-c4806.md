---
title: 编译器警告（等级 1） C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 5895e9bf489e240b1eff6f1499b711047ea74b9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175046"
---
# <a name="compiler-warning-level-1-c4806"></a>编译器警告（等级 1） C4806

“operation”：不安全的操作：提升到类型 “type” 的类型 “type” 没有值与给定的常量相等

此消息警告针对代码如 `b == 3`，其中 `b` 具有类型 `bool`。 提升规则使 `bool` 被提升为 `int`。 这是合法的但绝不为 **真**。 以下示例生成 C4806：

```cpp
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

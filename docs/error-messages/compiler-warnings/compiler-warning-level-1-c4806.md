---
title: 编译器警告（等级 1） C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 0d3b0aa05ca5fff16b3cd28c11e3bf8290de1b3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225340"
---
# <a name="compiler-warning-level-1-c4806"></a>编译器警告（等级 1） C4806

“operation”：不安全的操作：提升到类型 “type” 的类型 “type” 没有值与给定的常量相等

此消息警告代码 `b == 3` ，如，其中 `b` 具有类型 **`bool`** 。 升级规则将导致 **`bool`** 升级到 **`int`** 。 这是合法的，但永远不能 **`true`** 。 以下示例生成 C4806：

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

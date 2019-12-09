---
title: 编译器错误 C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: 6eed1f1aad0783f9e1d5f4126847b54f6b7278e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739193"
---
# <a name="compiler-error-c2798"></a>编译器错误 C2798

"super：： member" 不明确

多个继承结构包含用[super](../../cpp/super.md)引用的成员。 可以通过以下任一方法修复错误：

- 从 D 的继承列表中删除 B1 或 B2。

- 更改 B1 或 B2 中的数据成员的名称。

下面的示例生成 C2798：

```cpp
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```

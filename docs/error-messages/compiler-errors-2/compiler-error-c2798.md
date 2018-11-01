---
title: 编译器错误 C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463047"
---
# <a name="compiler-error-c2798"></a>编译器错误 C2798

super::member 不明确

多个继承的结构包含与所引用的成员[super](../../cpp/super.md)。 可以通过以下任一方法来修复此错误：

- D.在继承列表从删除 B1 或 B2

- 更改在 B1 或 B2 中的数据成员的名称。

下面的示例生成 C2798:

```
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
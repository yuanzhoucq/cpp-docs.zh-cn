---
title: 编译器错误 C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: e060c2b9a38866a898a3c5ada9e595464050877e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756092"
---
# <a name="compiler-error-c2657"></a>编译器错误 C2657

在语句的开始找到 "class：:*" （是否忘记指定类型？）

该行以指向成员的指针标识符开头。

如果指向成员的指针的声明中缺少类型说明符，则可能导致此错误。

下面的示例生成 C2657：

```cpp
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```

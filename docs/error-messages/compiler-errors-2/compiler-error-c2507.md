---
title: 编译器错误 C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 23433dccd7fc4f86c2e848359ac50c796fcccab0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746794"
---
# <a name="compiler-error-c2507"></a>编译器错误 C2507

"identifier"：基类上的虚拟修饰符太多

类或结构被声明为 `virtual` 多次。 对于基类列表中的每个类，只能出现一个 `virtual` 修饰符。

下面的示例生成 C2507：

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```

---
title: 编译器错误 C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 944eaeadb038e6466d65859f72900db164cfe34d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221154"
---
# <a name="compiler-error-c2507"></a>编译器错误 C2507

"identifier"：基类上的虚拟修饰符太多

一个类或结构被声明为多次 **`virtual`** 。 **`virtual`** 对于基类列表中的每个类，只能显示一个修饰符。

下面的示例生成 C2507：

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```

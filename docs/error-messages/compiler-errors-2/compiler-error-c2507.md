---
title: 编译器错误 C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 63f9594eb9ee8a251faafe7323418b343c03063c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618019"
---
# <a name="compiler-error-c2507"></a>编译器错误 C2507

identifier： 基类上的虚拟修饰符太多

类或结构声明为`virtual`不止一次。 只有一个`virtual`修饰符可以出现在列表中每个类的基类。

下面的示例生成 C2507:

```
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
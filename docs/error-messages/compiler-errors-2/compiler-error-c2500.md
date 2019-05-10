---
title: 编译器错误 C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: a5753fc99efcdb1064a21981c62faaba84d44189
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165581"
---
# <a name="compiler-error-c2500"></a>编译器错误 C2500

identifier1: identifier2 已经是直接基类

类或结构的基类列表中多次出现。

直接基是基列表中所述。 间接基是基类的基列表中的类之一。

类不能多次指定为直接基类。 可以多次作为间接基类使用类。

下面的示例生成 C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
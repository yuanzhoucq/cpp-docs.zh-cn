---
title: 编译器错误 C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746963"
---
# <a name="compiler-error-c2500"></a>编译器错误 C2500

"identifier1"： "identifier2" 已是直接基类

某个类或结构在基类列表中出现多次。

直接基是基列表中提到的一个。 间接基是基列表中某个类的基类。

不能将一个类多次指定为直接基类。 类可以多次用作间接基类。

下面的示例生成 C2500：

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```

---
title: 编译器错误 C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: f5a62b1c12b94735d0383697bf7a92d12d64b21f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757795"
---
# <a name="compiler-error-c2243"></a>编译器错误 C2243

存在从“类型 1”到“类型 2”的“转换类型”转换，但不可访问

访问保护（`protected` 或 `private`）已禁止从指向派生类的指针转换为指向基类的指针。

下面的示例生成 C2243：

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

派生类的客户端不能访问具有 `protected` 或 `private` 访问权限的基类。 这些级别的访问控制用于指示基类是对客户端不可见的实现细节。 如果你希望派生类的客户端有权访问派生类指针到基类指针的隐式转换，请使用公共派生。

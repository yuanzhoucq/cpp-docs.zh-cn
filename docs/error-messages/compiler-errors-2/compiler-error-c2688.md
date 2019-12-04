---
title: 编译器错误 C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: cc871467e1e3fb23edc6231c3adb182f5e26c0d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760239"
---
# <a name="compiler-error-c2688"></a>编译器错误 C2688

"C2：： fgrv"：对 varargs 函数不支持具有多个或虚拟继承的协变返回

当函数包含变量参数时，Visual C++返回类型不受 Visual 支持。

若要解决此错误，请定义函数，使它们不使用变量参数或使返回值对所有虚函数都是相同的。

下面的示例生成 C2688：

```cpp
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```

---
title: 编译器错误 C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 75e3b438dd69f8879fdc2273a8f0357229941340
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386897"
---
# <a name="compiler-error-c2594"></a>编译器错误 C2594

operator： 不明确的转换，从 type1 到 type2

没有从转换*type1*到*type2*比其他更直接。 我们建议从转换到的两个可能的解决方案*type1*到*type2*。 第一个选项是定义直接转换*type1*到*type2*，和第二个选项是指定的从一系列序列*type1*到*type2*。

下面的示例生成 C2594。 与该错误的建议解决方法是一系列转换：

```
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
---
title: 编译器错误 C2594 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2594
dev_langs:
- C++
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9be22544930bb94c36ec5906cbf60d5caac143fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058000"
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
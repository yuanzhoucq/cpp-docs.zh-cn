---
title: 编译器警告（等级1） C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 893364183594782b825377f57fa4e525338d62d8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052560"
---
# <a name="compiler-warning-level-1-c4630"></a>编译器警告（等级1） C4630

"symbol"：成员定义上的 "extern" 存储类说明符非法

数据成员或成员函数被定义为 `extern`。 成员不能是外部的，但整个对象都可以。 编译器将忽略 `extern` 关键字。 下面的示例生成 C4630：

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
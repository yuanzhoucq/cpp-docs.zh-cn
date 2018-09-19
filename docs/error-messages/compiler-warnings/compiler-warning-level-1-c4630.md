---
title: 编译器警告 （等级 1） C4630 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4630
dev_langs:
- C++
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dadfd4cd38d1b1d0e67e49e81102135a8ced1d00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054722"
---
# <a name="compiler-warning-level-1-c4630"></a>编译器警告（等级 1）C4630

symbol: extern 存储类说明符在成员定义上非法

数据成员或成员函数定义为`extern`。 成员不能为外部，尽管可以整个对象。 编译器将忽略`extern`关键字。 下面的示例生成 C4630:

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
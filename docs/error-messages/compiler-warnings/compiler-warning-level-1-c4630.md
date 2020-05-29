---
title: 编译器警告（等级 1）C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 414388fc1b9c6a7425d45e2ba92546960cadf404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199610"
---
# <a name="compiler-warning-level-1-c4630"></a>编译器警告（等级 1）C4630

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

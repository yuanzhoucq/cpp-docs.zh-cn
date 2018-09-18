---
title: 编译器错误 C3653 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3653
dev_langs:
- C++
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d0409317cb0cdf6a248554cba2e18d7f9d2e0e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018998"
---
# <a name="compiler-error-c3653"></a>编译器错误 C3653

function： 不能用作命名重写： 未找到; 被覆盖的函数是否忘记使用显式，命名该函数:: 运算符？

显式重写指定找不到任何界面中的函数。 有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。

下面的示例生成 C3653:

```
// C3653.cpp
// compile with: /clr
public interface struct I {
   void h();
};

public ref struct X : public I {
   virtual void f() new sealed = J {};   // C3653 no J in scope
   virtual void g() {}   // OK
   virtual void h() new sealed = I::h {};   // OK
};
```
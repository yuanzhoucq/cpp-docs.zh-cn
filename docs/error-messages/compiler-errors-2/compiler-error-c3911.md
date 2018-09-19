---
title: 编译器错误 C3911 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3911
dev_langs:
- C++
helpviewer_keywords:
- C3911
ms.assetid: b786da59-0e99-479d-bc0d-551126e940f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98b2b1b4712d71c5baa7179ce3c348ace3761bb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037380"
---
# <a name="compiler-error-c3911"></a>编译器错误 C3911

event_accessor_method： 函数必须具有类型签名

未正确声明事件访问器方法。

有关详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。

下面的示例生成 C3911:

```
// C3911.cpp
// compile with: /clr
using namespace System;
delegate void H(String^, int);

ref class X {
   event H^ E1 {
      void add() {}   // C3911
      // try the following line instead
      // void add(H ^ h) {}

      void remove(){}
      // try the following line instead
      // void remove(H ^ h) {}

      void raise(){}
      // try the following line instead
      // void raise(String ^ s, int i) {}
   };
};
```
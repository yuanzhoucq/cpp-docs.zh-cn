---
title: 编译器错误 C3265 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3265
dev_langs:
- C++
helpviewer_keywords:
- C3265
ms.assetid: 10ab3e17-4a9f-4120-bab5-21473869b70f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cd295611f483a97dcf3621a6a923ec5153232e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024133"
---
# <a name="compiler-error-c3265"></a>编译器错误 C3265

不能声明托管托管中构造的非托管的非托管构造

在非托管上下文中，不能包含托管的对象。

下面的示例重新产生 C3265:

```
// C3265_2.cpp
// compile with: /clr /LD
#include <vcclr.h>

ref class A { };

class B
// try the following line instead
// ref class B
{
   A ^a;   // C3265
   // or embed the managed handle using gcroot
   // try the following line instead
   // gcroot<A^> a;
};
```

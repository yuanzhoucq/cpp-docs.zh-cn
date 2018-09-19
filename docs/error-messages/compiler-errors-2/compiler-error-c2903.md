---
title: 编译器错误 C2903 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2903
dev_langs:
- C++
helpviewer_keywords:
- C2903
ms.assetid: bf6b223f-4921-48c7-82b9-ff318b42c801
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f06baeaa262905d36306e8e36985018db9eeb819
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091252"
---
# <a name="compiler-error-c2903"></a>编译器错误 C2903

“identifier”：符号既不是类模板也不是函数模板

代码尝试显式实例化非模板的内容。

以下示例生成 C2903：

```
// C2903.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template Y y;   // C2903
   N::X<N::Y> y;   // OK
}
```

当使用泛型时，也可能发生 C2903：

```
// C2903b.cpp
// compile with: /clr /c
namespace N {
   class Y {};
   generic<class T> ref class Z {};
}

void f() {
   N::generic Y y;   // C2903
   N:: generic Z<int>^ z;   // OK
}
```
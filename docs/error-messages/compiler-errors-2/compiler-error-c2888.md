---
title: 编译器错误 C2888
ms.date: 11/04/2016
f1_keywords:
- C2888
helpviewer_keywords:
- C2888
ms.assetid: 244f593e-ff25-4dad-b31f-84dafa3bc84a
ms.openlocfilehash: c5b547f1c4d62a6f48b6c5f8f901be309e81a67c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662899"
---
# <a name="compiler-error-c2888"></a>编译器错误 C2888

identifier： 不能在命名空间 namespace 中定义符号

必须包含 A.命名空间中定义属于命名空间的符号

下面的示例生成 C2888:

```
// C2888.cpp
// compile with: /c
namespace M {
   namespace N {
      void f1();
      void f2();
   }

   void N::f1() {}   // OK: namspace M encloses N
}

namespace O {
   void M::N::f2() {}   // C2888 namespace O does not enclose M
}
```
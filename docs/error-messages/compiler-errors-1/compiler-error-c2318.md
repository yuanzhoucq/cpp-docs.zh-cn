---
title: 编译器错误 C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: a68a333c9cb817a653597acb011dfbb9291c4d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615758"
---
# <a name="compiler-error-c2318"></a>编译器错误 C2318

没有与该 catch 处理程序关联的 Try 块

定义一个 `catch` 处理程序，但其前面没有 `try` 块。

以下示例生成 C2318：

```
// C2318.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   // no try block
   catch( int ) {}   // C2318
}
```

可能的解决方法：

```
// C2318b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try{}
   catch( int ) {}
}
```
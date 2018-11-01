---
title: 编译器错误 C2313
ms.date: 11/04/2016
f1_keywords:
- C2313
helpviewer_keywords:
- C2313
ms.assetid: f70eb19b-c0a3-4fb2-ade1-3890a589928d
ms.openlocfilehash: 276dea87770035967a08ca5ac3e95316832ffc1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641072"
---
# <a name="compiler-error-c2313"></a>编译器错误 C2313

“type1”：由引用（“type2”）在行号上捕获

异常类型有两个处理程序。 第二个 catch 的类型是对第一个类型的引用。

以下示例生成 C2313：

```
// C2313.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
    try {
        throw "ooops!";
    }
    catch( C& ) {}
    catch( C ) {}   // C2313
}
```
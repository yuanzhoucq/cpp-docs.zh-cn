---
title: 编译器警告（等级 4）C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 80794d270b40a8f40d44630da70455c015158423
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541241"
---
# <a name="compiler-warning-level-4-c4100"></a>编译器警告（等级 4）C4100

"identifier"：未引用的形参

函数体中未引用形参。 未引用的参数将被忽略。

当代码对基元类型的其他未引用参数调用析构函数时，也可以发出 C4100。  这是 Microsoft C++编译器的一个限制。

下面的示例生成 C4100：

```cpp
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```
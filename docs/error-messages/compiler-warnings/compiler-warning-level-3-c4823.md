---
title: 编译器警告（等级 3）C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: 28d490c341c4d14c2e6c03e13007b5a8be423622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625897"
---
# <a name="compiler-warning-level-3-c4823"></a>编译器警告（等级 3）C4823

function： 使用钉住指针但展开语义不会启用。 请考虑使用 /EHa

若要取消固定在块范围中声明钉住指针指向托管堆上的对象，编译器将模拟的"伪装"钉住指针具有析构函数，使该指针无效的局部类的析构函数的行为。 要启用对析构函数的调用引发异常后，你必须启用对象展开，可以通过执行此操作[/EHsc](../../build/reference/eh-exception-handling-model.md)。

可以手动取消固定对象，并忽略该警告。

## <a name="example"></a>示例

下面的示例生成 C4823。

```
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```

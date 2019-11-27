---
title: 编译器警告（等级 3）C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: a96877252b0b7699f5e4033f8e695f4d9016a6c9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541269"
---
# <a name="compiler-warning-level-3-c4823"></a>编译器警告（等级 3）C4823

"function"：使用钉住指针，但未启用展开语义。 考虑使用/EHa

若要取消固定托管堆上的对象（由块范围中声明的固定指针所指向的对象），编译器将模拟局部类的析构函数的行为，"伪装" 钉住指针具有 nullifies 指针的析构函数。 若要在引发异常后启用对析构函数的调用，则必须启用对象展开，这可以通过使用[/ehsc](../../build/reference/eh-exception-handling-model.md)来执行。

你还可以手动取消固定对象并忽略该警告。

## <a name="example"></a>示例

下面的示例生成 C4823。

```cpp
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

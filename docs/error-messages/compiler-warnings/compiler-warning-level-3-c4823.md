---
title: 编译器警告 （等级 3） C4823 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c3a6f24a32267f221dbc37e242bae48c0056af5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044647"
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

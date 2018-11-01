---
title: 编译器错误 C2473
ms.date: 11/04/2016
f1_keywords:
- C2473
helpviewer_keywords:
- C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
ms.openlocfilehash: 232f89a714d70c6914b73a370c5f658ff4283ab4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631785"
---
# <a name="compiler-error-c2473"></a>编译器错误 C2473

“identifier”: 看起来像函数定义，但却没有参数列表。

编译器检测到看似为函数、但没有参数列表的内容。

## <a name="example"></a>示例

下面的示例生成 C2473。

```
// C2473.cpp
// compile with: /clr /c
class A {
   int i {}   // C2473
};

class B {
   int i() {}   // OK
};
```
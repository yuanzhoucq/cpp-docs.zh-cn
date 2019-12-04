---
title: 编译器错误 C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 6b6f08ac52eff355f0857968817a681818e3c3dc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756768"
---
# <a name="compiler-error-c2556"></a>编译器错误 C2556

"identifier"：重载函数只在返回类型上不同

重载函数具有不同的返回类型，但具有相同的参数列表。 每个重载函数都必须具有一个不同的形参列表。

下面的示例生成 C2556：

```cpp
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```

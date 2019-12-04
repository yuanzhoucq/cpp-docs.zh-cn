---
title: 编译器错误 C3913
ms.date: 11/04/2016
f1_keywords:
- C3913
helpviewer_keywords:
- C3913
ms.assetid: a678bfce-9524-470d-9f23-7d08ecb972c8
ms.openlocfilehash: 0dfe8274c2b9ee5d2861239c8bb1464d9642ebc9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741256"
---
# <a name="compiler-error-c3913"></a>编译器错误 C3913

必须将默认属性编入索引

未正确定义默认属性。

有关详细信息，请参阅 [property](../../extensions/property-cpp-component-extensions.md)。

下面的示例生成 C3913：

```cpp
// C3913.cpp
// compile with: /clr /c
ref struct X {
   property int default {   // C3913
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```

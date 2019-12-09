---
title: 编译器错误 C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: a119f8a9482d3f49c98873fee6f54b434416ee48
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757574"
---
# <a name="compiler-error-c3282"></a>编译器错误 C3282

泛型参数列表只能出现在托管或 WinRTclasses、结构或函数上

未正确使用泛型参数列表。  有关详细信息，请参阅[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下例生成了 C3282，并演示了如何对其进行修复。

```cpp
// C3282.cpp
// compile with: /clr /c
generic <typename T> int x;   // C3282

ref struct GC0 {
   generic <typename T> int x;   // C3282
};

// OK
generic <typename T>
ref class M {};
```

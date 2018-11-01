---
title: 编译器错误 C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: 7092ddc3bf6859212cbb143572de1ef3604a13d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491502"
---
# <a name="compiler-error-c3282"></a>编译器错误 C3282

泛型参数列表只能出现在托管或 WinRTclasses、 结构或函数

未正确使用泛型参数列表。  有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>示例

下例生成了 C3282，并演示了如何对其进行修复。

```
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
---
title: 编译器错误 C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: 03fc7e9da8a9b3a2e2c445f5b06395c2616f0d98
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755429"
---
# <a name="compiler-error-c2581"></a>编译器错误 C2581

"type"：静态 "operator =" 函数是非法的

赋值（`=`）运算符错误地声明为 `static`。 不能 `static`赋值运算符。 有关详细信息，请参阅[用户定义的运算符C++（/cli）](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C2581。

```cpp
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```

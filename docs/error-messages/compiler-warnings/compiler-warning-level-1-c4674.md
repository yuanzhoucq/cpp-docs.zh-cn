---
title: 编译器警告（等级 1）C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: b9428a593ff59cbdfa6d8eb369413a560b4a5ad2
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052543"
---
# <a name="compiler-warning-level-1-c4674"></a>编译器警告（等级 1）C4674

“方法”应声明为“静态”，而且只能有一个参数

转换运算符的签名不正确。 该方法不被视为用户定义的转换。 有关定义运算符的详细信息，请参阅[用户定义的运算符C++（/Cli）](../../dotnet/user-defined-operators-cpp-cli.md)和[用户定义的转换C++（/cli）](../../dotnet/user-defined-conversions-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4674。

```cpp
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```

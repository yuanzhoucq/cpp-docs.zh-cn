---
title: 编译器警告（等级 1）C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: f7db2f37224a8defffb545b0cfaf018fd4654227
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374542"
---
# <a name="compiler-warning-level-1-c4674"></a>编译器警告（等级 1）C4674

“方法”应声明为“静态”，而且只能有一个参数

转换运算符的签名不正确。 该方法不被视为用户定义的转换。 有关定义运算符的详细信息，请参阅[用户定义的运算符 (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md)并[用户定义的转换 (C++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4674。

```
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```

---
title: 编译器警告 （等级 1） C4674 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b2f945982e80b49403387241f29a50876274e66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024874"
---
# <a name="compiler-warning-level-1-c4674"></a>编译器警告（等级 1）C4674

“方法”应声明为“静态”，而且只能有一个参数

转换运算符的签名不正确。 该方法不被视为用户定义的转换。 有关定义运算符的详细信息，请参阅[用户定义的运算符 (C + + CLI)](../../dotnet/user-defined-operators-cpp-cli.md)并[用户定义的转换 (C + + CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。

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

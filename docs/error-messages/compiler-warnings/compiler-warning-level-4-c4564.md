---
title: 编译器警告 （等级 C4564 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea8d392251c8168490d7841ad590731b5a08e7f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031829"
---
# <a name="compiler-warning-level-4-c4564"></a>编译器警告（等级 4）C4564

方法 method 类 class 的定义不支持的默认参数 parameter

编译器检测到具有一个或多个参数具有默认值的方法。 调用此方法; 将忽略为参数的默认值显式指定这些参数的值。 如果未显式指定这些参数的值，c + + 编译器将生成错误。

给定的用 Visual Basic 创建以下.dll 文件的情况下，表示允许为默认参数方法自变量：

```
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

和使用 Visual Basic 中，使用创建的.dll 文件的以下 c + + 示例

```
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```
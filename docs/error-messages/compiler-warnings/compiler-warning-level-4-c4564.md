---
title: 编译器警告（等级 4）C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: f5db6bf366c86a716be33539feb0085ac03a9647
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683163"
---
# <a name="compiler-warning-level-4-c4564"></a>编译器警告（等级 4）C4564

类 "class" 的方法 "method" 定义了不受支持的默认参数 "parameter"

编译器检测到有一个或多个参数具有默认值的方法。 调用方法时将忽略参数的默认值;显式指定这些参数的值。 如果未显式指定这些参数的值， C++编译器将生成错误。

给定以下 .dll Visual Basic 创建，这将允许方法参数上的默认参数：

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

下面C++的示例使用使用创建的 .dll Visual Basic

```cpp
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
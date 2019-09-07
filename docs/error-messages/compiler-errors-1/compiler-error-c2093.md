---
title: 编译器错误 C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741145"
---
# <a name="compiler-error-c2093"></a>编译器错误 C2093

"variable1"：无法使用自动变量 "变量 2" 的地址初始化

使用[/za](../../build/reference/za-ze-disable-language-extensions.md)进行编译时，程序试图使用自动变量的地址作为初始值设定项。

下面的示例生成 C2093：

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```
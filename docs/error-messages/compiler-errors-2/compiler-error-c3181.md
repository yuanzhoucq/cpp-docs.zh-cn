---
title: 编译器错误 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781804"
---
# <a name="compiler-error-c3181"></a>编译器错误 C3181

type： 运算符的操作数无效

无效的参数传递给[typeid](../../extensions/typeid-cpp-component-extensions.md)运算符。 参数必须是托管的类型。

请注意，编译器使用的本机类型将映射到公共语言运行时中的类型的别名。

下面的示例生成 C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```

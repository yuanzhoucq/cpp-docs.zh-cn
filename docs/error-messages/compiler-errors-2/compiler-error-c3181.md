---
title: 编译器错误 C3181 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3181
dev_langs:
- C++
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 599fe0afe4bdcdc7b1e2025859d11a38618b1349
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097336"
---
# <a name="compiler-error-c3181"></a>编译器错误 C3181

type： 运算符的操作数无效

无效的参数传递给[typeid](../../windows/typeid-cpp-component-extensions.md)运算符。 参数必须是托管的类型。

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

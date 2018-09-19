---
title: 编译器错误 C3255 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3255
dev_langs:
- C++
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f77ad1530b59c01d36a7144e2074a4b1731a9db3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043477"
---
# <a name="compiler-error-c3255"></a>编译器错误 C3255

值类型： 不能动态地分配本机堆上的此值类型对象

值类型的实例 (请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)) 包含托管的成员可以在堆栈上，但不是在堆上创建。

下面的示例生成 C3255:

```
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```

---
title: 编译器错误 C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 129d2698a782d2b98267877e8d575a6ee641b94b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778210"
---
# <a name="compiler-error-c3255"></a>编译器错误 C3255

值类型： 不能动态地分配本机堆上的此值类型对象

值类型的实例 (请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)) 包含托管的成员可以在堆栈上，但不是在堆上创建。

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

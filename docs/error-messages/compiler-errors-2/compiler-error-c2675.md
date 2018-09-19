---
title: 编译器错误 C2675 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1772f6e88516e7c8c1498f84d180ab6c4e0e05ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102389"
---
# <a name="compiler-error-c2675"></a>编译器错误 C2675

一元 operator: type 不定义该运算符或到可接受类型转换到预定义的运算符

当使用一元运算符，也会发生 C2675 和类型未定义操作员或可接受的类型转换到预定义的运算符。 要使用该运算符，必须针对指定类型将其重载，或者定义一个到某个类型（该运算符已针对此类型进行了定义）的转换。

## <a name="example"></a>示例

下面的示例生成 C2675。

```
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```
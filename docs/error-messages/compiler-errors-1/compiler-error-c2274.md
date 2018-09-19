---
title: 编译器错误 C2274 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2274
dev_langs:
- C++
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fcc6b0afe78e089c268f69274be1cbfb6f3d32c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093191"
---
# <a name="compiler-error-c2274"></a>编译器错误 C2274

type： 非法的右边。 ' 运算符

类型显示为成员访问 （.） 运算符的右操作数。

通过尝试访问用户定义类型转换可以导致此错误。 使用关键字`operator`之间的这段和`type`。

下面的示例生成 C2286：

```
// C2274.cpp
struct MyClass {
   operator int() {
      return 0;
   }
};

int main() {
   MyClass ClassName;
   int i = ClassName.int();   // C2274
   int j = ClassName.operator int();   // OK
}
```
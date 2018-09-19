---
title: 编译器错误 C2513 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82df537e49ca17140d70977486314f43a072022d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045427"
---
# <a name="compiler-error-c2513"></a>编译器错误 C2513

type: = 前没有声明变量

类型说明符出现在声明中不带任何变量的标识符。

下面的示例生成 C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

此错误也生成的 Visual Studio.NET 2003年完成编译器一致性工作： 不再允许 typedef 的初始化。 Typedef 的初始化不允许标准，现在会生成编译器错误。

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

一种替代方法就是删除`typedef`可定义与聚合初始值设定项列表中，而此变量不建议，因为它将创建具有相同名称作为类型的变量和隐藏的类型名称。
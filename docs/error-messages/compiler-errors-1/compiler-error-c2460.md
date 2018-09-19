---
title: 编译器错误 C2460 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb2d85ffbc7aa799f0688fbb10021a04ef9455ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022599"
---
# <a name="compiler-error-c2460"></a>编译器错误 C2460

identifier1： 使用 identifier2，正在定义的

类或结构 (`identifier2`) 声明为其自身的成员 (`identifier1`)。 不允许递归定义的类和结构。

下面的示例生成 C2460:

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

相反，在类中使用的指针引用。

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```
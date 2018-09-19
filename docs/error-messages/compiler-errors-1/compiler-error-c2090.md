---
title: 编译器错误 C2090 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2090
dev_langs:
- C++
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613d3214e652e994ec07e1fe4396b4eb15798067
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028774"
---
# <a name="compiler-error-c2090"></a>编译器错误 C2090

函数返回数组

函数不能返回数组。 而是返回指向数组的指针。

下面的示例生成 C2090:

```
// C2090.cpp
int func1(void)[] {}   // C2090
```

可能的解决方法：

```
// C2090b.cpp
// compile with: /c
int* func2(int * i) {
   return i;
}
```
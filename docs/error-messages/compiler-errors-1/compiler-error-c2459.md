---
title: 编译器错误 C2459 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2459
dev_langs:
- C++
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b67c5ba4c714b096da58b1e4d837840dc6b5fd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113209"
---
# <a name="compiler-error-c2459"></a>编译器错误 C2459

identifier： 正在定义;不能添加作为匿名成员

类、 结构或联合内重新定义其自己范围的匿名联合成员。

下面的示例生成 C2459:

```
// C2459.cpp
// compile with: /c
class C {
   union { int C; };   // C2459
   union { int D; };
};
```
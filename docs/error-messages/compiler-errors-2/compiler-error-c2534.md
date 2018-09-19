---
title: 编译器错误 C2534 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2534
dev_langs:
- C++
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2febeeeb3b6c0e394070339f2310a22c1326ab5c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049028"
---
# <a name="compiler-error-c2534"></a>编译器错误 C2534

identifier： 构造函数无法返回值

构造函数不能返回值或具有返回类型 (甚至不能`void`返回类型)。

通过删除可能会修复此错误`return`从构造函数定义的语句。

下面的示例生成 C2534:

```
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
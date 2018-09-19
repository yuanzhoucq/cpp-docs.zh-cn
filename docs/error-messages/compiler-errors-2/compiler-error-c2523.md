---
title: 编译器错误 C2523 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2523
dev_langs:
- C++
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77f440bf282d6159af3a96bfeb1aa7db8941e87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022794"
---
# <a name="compiler-error-c2523"></a>编译器错误 C2523

类:: ~ 标识符： 析构函数/终结器标记不匹配

析构函数的名称必须是类名前面是波形符 (`~`)。 构造函数和析构函数具有与类相同的名称的唯一成员。

下面的示例生成 C2523:

```
// C2523.cpp
// compile with: /c
class A {
   ~B();    // C2523
   ~A();   // OK
};
```